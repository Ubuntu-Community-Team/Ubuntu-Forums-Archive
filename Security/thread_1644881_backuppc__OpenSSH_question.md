---
title: "backuppc / OpenSSH question"
date: 2010-12-13
forum: Security
---

### Post by click4851 on 2010-12-13
So I am struggling with setting up BackupPC to backup a linux pc, all connected via a wired router. I will be using rsync and openSSH. Basically I following this howto: [http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc)

where I am struggling is (page 4.) the confirmation of the passwordless login as root of user *backuppc*. It fails and I'm not sure why, two areas I'm alittle hazy on. One is the use by the author of the ~ symbol. Unfortunately I never use it, so I'm a bit ignorant. the other concerns the sending of backuppc's pub key to the client.

cp ~/.ssh/id_rsa.pub ~/.ssh/BackupPC_id_rsa.pub
scp ~/.ssh/BackupPC_id_rsa.pub [email]root@192.168.0.213:/root/.ssh[/email]/

The authenticity of host '192.168.0.213 (192.168.0.213)' can't be established.
RSA key fingerprint is 9b:66:3e:ce:b4:8d:63:00:ba:87:14:b2:94:03:cb:a8.
Are you sure you want to continue connecting (yes/no)? <-- yes
**Warning: Permanently added '192.168.0.213' (RSA) to the list of known hosts.**root@192.168.0.213's password: <-- root password for falko-desktop 
BackupPC_id_rsa.pub 100% 410 0.4KB/s 00:00 

when I do this it adds the key to known_hosts in my client /home directory, not its /root/.ssh directory where everything else is.

I guess I wondering if in this case, in each respective location should known_hosts file be in the default location (/home/user), or 

server: /var/lib/backuppc/.ssh
client: /root/.ssh 

with the rest of the files in that directory?

also ~, is this the authors way of avoiding typing the explicit file location, or does it mean something else?

---

### Post by bodhi.zazen on 2010-12-14
~ is short hand for your home directory.

---

### Post by click4851 on 2010-12-14
thats what I have read as well. All the more confusing when the author does this:

[I]Next we create a private/public key pair on server1.example.com. We must do this as the user backuppc!

server1.example.com:

su backuppc
ssh-keygen -t rsa

Generating public/private rsa key pair.
Enter file in which to save the key (/var/lib/backuppc/.ssh/id_rsa): <-- <ENTER>
Created directory '/var/lib/backuppc/.ssh'.
Enter passphrase (empty for no passphrase): <-- <ENTER>
Enter same passphrase again: <-- <ENTER>
Your identification has been saved in /var/lib/backuppc/.ssh/id_rsa.
Your public key has been saved in /var/lib/backuppc/.ssh/id_rsa.pub.
The key fingerprint is:
74:20:65:73:47:1c:cb:ba:5d:9b:5d:56:cf:91:1a:1a [email]backuppc@server1.example.com[/email]

Then we copy the public key to falko-desktop. Make sure you use falko-desktop's current IP address in the scp command:

server1.example.com:

cp ~/.ssh/id_rsa.pub ~/.ssh/BackupPC_id_rsa.pub
scp ~/.ssh/BackupPC_id_rsa.pub [email]root@192.168.0.213:/root/.ssh[/email]/[/I]

He creates a pair of keys in /var/lib/backuppc/.ssh, then in his cp command he writes "~/.ssh/id_rsa.pub ~/.ssh/BackupPC_id_rsa.pub"

what happened there, one minute were in /var the next were in /home?

---

### Post by bodhi.zazen on 2010-12-14
> **click4851 said:**
> thats what I have read as well. All the more confusing when the author does this:

[I]Next we create a private/public key pair on server1.example.com. We must do this as the user backuppc!

server1.example.com:

su backuppc
ssh-keygen -t rsa

Generating public/private rsa key pair.
Enter file in which to save the key (/var/lib/backuppc/.ssh/id_rsa): <-- <ENTER>
Created directory '/var/lib/backuppc/.ssh'.
Enter passphrase (empty for no passphrase): <-- <ENTER>
Enter same passphrase again: <-- <ENTER>
Your identification has been saved in /var/lib/backuppc/.ssh/id_rsa.
Your public key has been saved in /var/lib/backuppc/.ssh/id_rsa.pub.
The key fingerprint is:
74:20:65:73:47:1c:cb:ba:5d:9b:5d:56:cf:91:1a:1a [email]backuppc@server1.example.com[/email]

Then we copy the public key to falko-desktop. Make sure you use falko-desktop's current IP address in the scp command:

server1.example.com:

cp ~/.ssh/id_rsa.pub ~/.ssh/BackupPC_id_rsa.pub
scp ~/.ssh/BackupPC_id_rsa.pub [email]root@192.168.0.213:/root/.ssh[/email]/[/I]

He creates a pair of keys in /var/lib/backuppc/.ssh, then in his cp command he writes "~/.ssh/id_rsa.pub ~/.ssh/BackupPC_id_rsa.pub"

what happened there, one minute were in /var the next were in /home?

LOL

Some tutorials are harder to follow then others.

Also, to copy keys, use ssh-copy-id 

much much easier and less prone to errors.

Make sure the keys work, then disable password authentication (for ssh).

[http://bodhizazen.net/Tutorials/SSH_keys#ssh-copy-id](http://bodhizazen.net/Tutorials/SSH_keys#ssh-copy-id)

---

### Post by click4851 on 2010-12-14
my first thought was this:

[I]Tilde(~) as a separate word, expands to $HOME if it is defined, if $HOME is not defined, then it expands with the home directory of the current user.

Now the value of the HOME variable is /home/oracle so cd ~ changed the current directory to the value of $HOME.[/I]

I thought maybe he had "defined" $HOME on both the client (/root/.ssh)and the server (/var/lib/backuppc/.ssh)

---

### Post by click4851 on 2010-12-14
thank you for the link, most helpful. One last question if I may.
Pertains to contents of the .ssh file. Should everything ssh related be in one directory? keys, known_hosts, authorized_keys2..etc. So on the client in my example, everything related to .ssh should be in /root/.ssh, similarly on the server, everything .ssh related should be in /var/lib/backuppc/.ssh

---

### Post by bodhi.zazen on 2010-12-14
".ssh" is a (configuration) directory.

Configuration files and directories are in several potential locations.

System wide settings are in /etc , /etc/bash for your (bash) shell and for many ssh settings /etc/ssh.

Users may have their own, personal customizations in their home directories, say ~/.bashrc (and other config files for bash such as ~/.profile) or in the case of ssh, ~/.ssh

Typically ~/.ssh stores

ssh keys
known_hosts
configuration settings

So, /root/.ssh is the default location for root's ssh keys / settings

~/.ssh is for your user.

Things in /etc or other locations are used by the system, for example host keys.

Much of this can be configured for alternate locations, the above is simply the default behavior. See /etc/ssh/sshd_config and /etc/ssh/ssh_config for options / default settings .

"/var/lib/backuppc/.ssh" is specific to the how to you are following. You could likely use an alternate location, such as /etc/backuppc/.ssh (but you would need to configure your backup to use that alternate location).

HTH

---

### Post by click4851 on 2010-12-14
it does, many thanks for your time....

---

### Post by click4851 on 2010-12-14
middle of the morning here update. After our discussion of all thing SSH I was still getting prompted for a password. So I reread our conversation and reread the walkthrough. I ran across this command:

ssh -l root -vvvv 129.168.X.X whoami

and I was able to get enough info from SSH to figure out my mistake on the server side. I had indeed created the keys in /var/lib/backuppc....., but nowhere does the author talk about updating ssh/sshd conf files to reflect their other than default location. SSH still expected to see them in /home/backuppc/.ssh (or I supppose ~/.ssh). Moved them there, checked/changed permissions and viola. Passwordless login from server to client.

Thanks again

---

### Post by bodhi.zazen on 2010-12-14
> **click4851 said:**
> middle of the morning here update. After our discussion of all thing SSH I was still getting prompted for a password. So I reread our conversation and reread the walkthrough. I ran across this command:

ssh -l root -vvvv 129.168.X.X whoami

and I was able to get enough info from SSH to figure out my mistake on the server side. I had indeed created the keys in /var/lib/backuppc....., but nowhere does the author talk about updating ssh/sshd conf files to reflect their other than default location. SSH still expected to see them in /home/backuppc/.ssh (or I supppose ~/.ssh). Moved them there, checked/changed permissions and viola. Passwordless login from server to client.

Thanks again

Glad you got it working =)

You might like some of the other content on my web page re: ssh.

Be sure to understand security =)

[http://bodhizazen.net/Tutorials/SSH_overview](http://bodhizazen.net/Tutorials/SSH_overview)

---

