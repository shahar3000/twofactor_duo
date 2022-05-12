# twofactor_duo
Experimental Duo two-factor auth provider for Nextcloud

## Configuration
Add your duo configuration to your Nextcloud's `config/config.php` file (before `),;` at the end):
```
  'twofactor_duo' =>
  array (
          'IKEY' => 'xxx',
          'SKEY' => 'yyy',
          'HOST' => 'zzz',
          'AKEY' => 'nnn',
  ),
```
IKEY, SKEY and HOST should be taken from duo. when configuring the app, `Web SDK` should be selected.
<br>
AKEY can be generated using the command `dd if=/dev/random count=1 | sha256sum`

## Install
Copy the repository content to Nextcloud `custom_apps` directory.

## Commands
* App enable `docker exec -u www-data nextcloud php occ app:enable twofactor_duo`
* App disable `docker exec -u www-data nextcloud php occ app:disable twofactor_duo`
* App remove `docker exec -u www-data nextcloud php occ app:remove twofactor_duo`
* Clean app from registery `docker exec -u www-data nextcloud php occ twofactorauth:cleanup duo`
* Enable per user `docker exec -u www-data nextcloud php occ twofactorauth:enable <user_id> duo`
* Disable per user `docker exec -u www-data nextcloud php occ twofactorauth:disable <user_id> duo`
