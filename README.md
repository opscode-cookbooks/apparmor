# apparmor Cookbook

[![Cookbook Version](https://img.shields.io/cookbook/v/selnux.svg)](https://supermarket.chef.io/cookbooks/apparmor)
[![CI State](https://github.com/sous-chefs/apparmor/workflows/ci/badge.svg)](https://github.com/sous-chefs/apparmor/actions?query=workflow%3Aci)
[![OpenCollective](https://opencollective.com/sous-chefs/backers/badge.svg)](#backers)
[![OpenCollective](https://opencollective.com/sous-chefs/sponsors/badge.svg)](#sponsors)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](https://opensource.org/licenses/Apache-2.0)

Default recipe installs and manages AppArmor service, or disables and removes AppArmor depending on `default['apparmor']['disable']` attribute. Also includes a custom resource (LWRP) for managing AppArmor policies.

## Requirements

### Platforms

- Ubuntu
- Debian

### Chef

- Chef 12.7+

### Cookbooks

- none

## Attributes

- `default['apparmor']['disable']`: Controls installing or removing apparmor service in the `default.rb` recipe. Defaults to false which installs apparmor, starts the service, and enables the service.

## Recipes

### default.rb

This recipe either installs or removes the apparmor package and starts / enables the service depending on the state of `default['apparmor']['disable']`.

## Custom Resources

The following resources are provided:

- [apparmor_policy](documentation/apparmor_policy.md)

### Policy

Adds or removes Apparmor policies

#### Actions

- :add: Adds a new Apparmor policy using a provided policy file
- :remove: Removes a specified Apparmor policy

#### Properties

- :name: Name attribute. The name of the policy as stored in /etc/apparmor.d/.
- :source_cookbook: Cookbook to source the policy file from if the provider is not in the same cookbook.
- :source_filename: Name of the source file in the cookbook if it doesn't match the name attribute.

#### Examples

Add the policy my_super_app where a cookbook file exists in the same cookbook and is named my_super_app

```ruby
apparmor_policy 'my_super_app'
```

Add the policy my_super_app where a cookbook file exists in a different cookbook and the file is named my_super_app_am_policy

```ruby
apparmor_policy 'my_super_app' do
  source_cookbook 'acme_apparmor_profiles'
  source_filename 'my_super_app_am_policy'
end
```

Remove the policy my_super_app

```ruby
apparmor_policy 'my_super_app' do
  action  :remove
end
```

## Maintainers

This cookbook is maintained by the Sous Chefs. The Sous Chefs are a community of Chef cookbook maintainers working together to maintain important cookbooks. If you’d like to know more please visit [sous-chefs.org](https://sous-chefs.org/) or come chat with us on the Chef Community Slack in [#sous-chefs](https://chefcommunity.slack.com/messages/C2V7B88SF).


## Contributors

This project exists thanks to all the people who [contribute.](https://opencollective.com/sous-chefs/contributors.svg?width=890&button=false)

### Backers

Thank you to all our backers!

![https://opencollective.com/sous-chefs#backers](https://opencollective.com/sous-chefs/backers.svg?width=600&avatarHeight=40)

### Sponsors

Support this project by becoming a sponsor. Your logo will show up here with a link to your website.

![https://opencollective.com/sous-chefs/sponsor/0/website](https://opencollective.com/sous-chefs/sponsor/0/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/1/website](https://opencollective.com/sous-chefs/sponsor/1/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/2/website](https://opencollective.com/sous-chefs/sponsor/2/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/3/website](https://opencollective.com/sous-chefs/sponsor/3/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/4/website](https://opencollective.com/sous-chefs/sponsor/4/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/5/website](https://opencollective.com/sous-chefs/sponsor/5/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/6/website](https://opencollective.com/sous-chefs/sponsor/6/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/7/website](https://opencollective.com/sous-chefs/sponsor/7/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/8/website](https://opencollective.com/sous-chefs/sponsor/8/avatar.svg?avatarHeight=100)
![https://opencollective.com/sous-chefs/sponsor/9/website](https://opencollective.com/sous-chefs/sponsor/9/avatar.svg?avatarHeight=100)
