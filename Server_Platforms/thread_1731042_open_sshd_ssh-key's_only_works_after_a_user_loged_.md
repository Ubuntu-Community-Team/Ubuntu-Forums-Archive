---
title: "open sshd ssh-key's only works after a user loged in"
date: 2011-04-16
forum: Server Platforms
---

### Post by highspider on 2011-04-16
I have keys set up on ubuntu server 10.10
 When I issue "It failes for publickey"```
ssh -i ~/.ssh/id_rsa USERNAME@MYSITE -v
``````
...skip...
debug1: Authentications that can continue: [COLOR=Blue]publickey,[COLOR=Red]password[/COLOR][/COLOR]
debug1: Next authentication method:[COLOR=Blue] publickey[/COLOR]
debug1: Offering public key: /home/keegan/.ssh/id_rsa
debug1: Authentications that can continue: [COLOR=Blue]publickey[COLOR=Red],[/COLOR][/COLOR][COLOR=Red]password[/COLOR]
debug1: Next authentication method: [COLOR=Red]password[/COLOR]
USRNAME@MYSITE password: xxxxxxxxxxxxxxxxxxxxxxxxxxxx
debug1:[COLOR=Red] Authentication succeeded (password).[/COLOR]
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.utf8
```I login with password and I'm in (NOT PASS-PHRASE) 

while logged into the Server In one widow I can open a new Desktop shell 
and boom Pharse login with ssh-keys works fine.
```
ssh -i ~/.ssh/id_rsa USERNAME@MYSITE -v
..skip..
debug1: Authentications that can continue: [COLOR=Blue]publicke[/COLOR]y,[COLOR=Red]password[/COLOR]
debug1: Next authentication method: [COLOR=Blue]publickey[/COLOR]
debug1: Offering public key: /home/USERNAME/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug1: [COLOR=Blue]Authentication succeeded (publickey).[/COLOR]
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.utf8

```my permissions are```

ls -ld .ssh .ssh/* .
drwxr-xr-x 5 USERNAME USERNAME 4096 2011-04-14 12:21 .
drwxr-xr-x 2 USERNAME USERNAME 4096 2011-04-11 07:49 .ssh
-rw-r--r-- 1   USERNAME USERNAME  392 2011-04-10 00:56 .ssh/authorized_keys
-rw-r--r-- 1   USERNAME USERNAME  442 2011-04-11 07:49 .ssh/known_hosts

```Im tiring to get rid of sshd password login all together but can't I until I fix's this.

---

### Post by highspider on 2011-04-16
home folder encryption was the error.
 
since the home folder is encrypted the user has to be logged in first (home decrypted) in order for keys to be located and read in the home folder.

```

[COLOR=Navy]move the users old keys to a new dir (out of the encrypted home folder)[/COLOR]
sudo mkdir -m 0755 -p /etc/ssh/keys
sudo mkdir -m 0755 -p /etc/ssh/keys/$USER
sudo mv ~/.ssh/* /etc/ssh/keys/$USER
[COLOR=Navy]set up the ssh_config[/COLOR]
sudo sed -i 's/%h\/.ssh/\/etc\/ssh\/keys\/%u/g' /etc/sshd_config
```if someone doesn't understand 'sed' just edit line in /etc/ssh_config to read as 
AuthorizedKeysFile       /etc/ssh/keys/%u/authorized_keys

---

### Post by stmiller on 2011-04-16
Yeah this is a big problem often discussed with no good solution.

Here is one work around:

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427/comments/12](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427/comments/12)

---

