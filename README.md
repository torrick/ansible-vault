# Vault

Install, configure and maintain [Vault](https://www.vaultproject.io) - a tool
for managing secrets from HashiCorp.

## Role Philosophy

Please see
[ansible-consul](https://github.com/nahsi/ansible-consul#role-philosophy).

## Role Variables

See [defaults/](https://github.com/nahsi/ansible-vault/blob/master/defaults/) for details and examples.

#### `vault_version`

- version to use

#### `vault_dirs`

- a map of directories to create
- default:

```yaml
vault_dir: "/opt/vault"
vault_dirs:
  main:
    path: "{{ vault_dir }}"
  configs:
    path: "{{ vault_dir }}/config.d"
  certs:
    path: "{{ vault_dir }}/certs"
  data:
    path: "/var/lib/vault"
    mode: "u=rwX,g=rX,o="
  logs:
    path: "/var/log/vault"
```

#### `vault_config`

- main [configuration](https://www.vaultproject.io/docs/configuration) file
- example: please see [defaults/example.yml](https://github.com/nahsi/ansible-vault/blob/master/defaults/example.yml)

#### `vault_configs`

- map of configuration files to create in `config.d` directory. Restart on
  changes

#### `vault_user`

- owner of Vault process and files
- default: `vault`

#### `vault_group`

- group of `vault_user`
- default: `vault`

#### `vault_download_url`

- url to get Vault archive from
- default: `https://releases.hashicorp.com`

#### `vault_service`

- openrc service file
- default: see [defaults/main.yml](https://github.com/nahsi/ansible-vault/blob/master/defaults/main.yml)

#### `vault_unitfile`

- systemd unit file
- default: see [defaults/main.yml](https://github.com/nahsi/ansible-vault/blob/master/defaults/main.yml)

#### `skip_handlers`

- skip Vault restart/reload - useful when building images with Packer
- default: `false`

## Tags

- `config` - update Vault unit/service file and sync configuration files

## Author

- **Anatoly Laskaris** - [nahsi](https://github.com/nahsi)
