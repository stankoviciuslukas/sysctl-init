# ansible-sysctl

[![Build Status](https://travis-ci.com/paysera/ansible-sysctl?branch=master)](https://travis-ci.com/paysera/ansible-sysctl)

Ansible role managing modprobe modules and sysctl values on Debian/Ubuntu platforms.

## Requirements

None.

## Role Variables

Define list of modules to load to kernel.

```
kernel_modules:
  - name: nf_conntrack
```

If modules requires custom parameters role had additional section to define parameters. This section can be used without explicitly defining kernel_modules.

```
kernel_module_params:
  - name: nf_conntrack
    params:
      - name: hashsize
        value: "2048"
```

List of sysctl settings to enable in runtime.

```
sysctl_settings:
  - name: net.netfilter.nf_conntrack_max
    value: 65536
```

## Dependencies

None.

## Example Playbook

```
- hosts: all
    roles:
    - ansible-sysctl
    vars:
    kernel_modules:
        - name: nf_conntrack
        - name: 8021q

    kernel_module_params:
        - name: nf_conntrack
        params:
            - name: hashsize
            value: "1024"

    sysctl_settings:
        - name: net.netfilter.nf_conntrack_max
        value: 65536
```

## License

MIT / BSD
