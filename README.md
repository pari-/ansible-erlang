# erlang

[![Build Status](https://travis-ci.org/pari-/ansible-erlang.svg?branch=master)](https://travis-ci.org/pari-/ansible-erlang)

An Ansible role which installs and configures erlang

<!-- toc -->

- [Requirements](#requirements)
- [Example](#example)
- [Defaults](#defaults)
- [Dependencies](#dependencies)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: stretch). It is assumed to work on other Debian distributions as well.

Ansible version compatibility:

- __2.4.3.0__ (current version in use for development of this role) 
- 2.3.3.0
- 2.2.3.0
- 2.1.6.0

## Example

```yaml
---

- hosts: "all"
  roles:
    - role: "ansible-erlang"
      tags:
        - "erlang"

```

## Defaults

Available variables are listed below, along with default values (see defaults/main.yml). They're generally prefixed with `erlang_` (which I deliberately leave out here for better formatting).

variable | default | notes
-------- | ------- | -----
`cache_valid_time` | `3600` | `Update the apt cache if its older than the set value (in seconds)`
`default_release` | `{{ ansible_distribution_release\|lower }}` | `The default release to install packages from`
`package_list` | `['erlang']` | `The list of packages to be installed`
`pre_default_release` | `{{ erlang_default_release }}` | `The default release to install packages (pre_package_list) from`
`pre_package_list` | `['apt-transport-https','ca-certificates']` | `The list of prerequisite packages to be installed`
`repo_list[0]['repo']` | `deb https://packages.erlang-solutions.com/debian {{ erlang_default_release }} contrib` | `Source string for the repositories`
`repo_list[0]['repo']['key']['id']` | `D208507CA14F4FCA` | `Identifier of (the repository) key`
`repo_list[0]['repo']['key']['keyserver']` | `keyserver.ubuntu.com` | `Keyserver to retrieve the key (for the repository) from`
`supported_distro_list` | `['jessie', 'stretch']` | `A list of distribution releases this role supports`
`update_cache` | `yes` | `Run the equivalent of apt-get update before the operation`

## Dependencies

None

## License

MIT

## Author Information

* Patrick Ringl