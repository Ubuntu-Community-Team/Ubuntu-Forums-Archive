---
title: "Problem with RSA/DSA password-less authentication on Intrepid"
date: 2009-01-22
forum: Security
---

### Post by mirix on 2009-01-22
Hello,

I need to set up password-less ssh authentication in order to run parallel calculations in several nodes.

I have done this in the past with Hardy, just by following this how-to:

[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

However, for these instructions to work in Hardy I needed to uninstall the lsh packages and install the openssh packages.

In a different server running Intrepid nothing works. I have verified that /etc/ssh/sshd_config contain the lines:

RSAAuthentication yes
PubkeyAuthentication yes

I have changed the permissions of the .ssh directory and the authorized_keys files. I have created both DSA and RSA keys (each of them independently and both at the same time). I have created authorized_keys and authorized_keys2 files. I have played with the option

AuthorizedKeysFile	%h/.ssh/authorized_keys

in /etc/ssh/sshd_config

I have tried all possible combinations of installing and uninstalling openssh and lsh. 

Nothing works and I do not know what else could I possibly do.

Could anyone please help me to diagnose the problem?

Kind regards,

Miro

---

### Post by mirix on 2009-01-22
Update: In fact, the procedure:

[https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins](https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins)

does work in my 32 bit Intrepid laptop (password-less ssh login on localhost), but not in my 64 bit Intrepid server.

---

### Post by mirix on 2009-01-22
Ok, I solved the problem.

This is my how-two to password-less ssh (openssh) login in Ubuntu using a RSA key. There are many how-to like this around, but this is the one that worked for me in Ubuntu Intrepid Ibex.

Please, be aware that using password-less login in this was implicates security risks. Anyone having access to your account in your client could have access to the servers as well.

Ubuntu installs lsh by default. I do not know how to do the set up for lsh and, therefore, I had uninstalled it to install openssh. This requires root privileges. In the other how-to I have read there is no mention to the lsh issue. I guess there should be a better way to deal with this problem, but I ignore it.

In the SERVER:

1) Deinstall lsh-server (I have also deinstalled lsh-client and lsh-utils).

2) Install openssh-server and open-client.

3) Reboot.

Be aware that, by doing this the SSH host keys of the server change and therefore you will have to change the appropriate values in 

$HOME/.ssh/known_hosts

in each computer for which this server is a known host (including itself). If you do not know what I am talking about, do not worry. Next time you use any ssh related protocol to log into this server you will receive the more or less self-explanatory eves-droping scary message.

Do the usual stuff in the CLIENT ([https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins):](https://help.ubuntu.com/community/AdvancedOpenSSH#RSA%20Key-Based%20SSH%20Logins):)

4) ssh-keygen -t rsa

(you can use a password or leave it blank, depending if you need a completely password-less login or not). 

5) ssh-copy-id -i ~/.ssh/id_rsa.pub username@host

where username is your user name and host is the host name or IP of your server.

You are DONE.

If you run into TROUBLES, VERIFY (all this are the defaults in Ubuntu, but just check in case that you or somebody else had been altering something) in the SERVER that the file:

/etc/ssh/sshd_config

contains the lines:

RSAAuthentication yes
PubkeyAuthentication yes

and that they are uncommented (remove the # at the begining if necessary). This requires root privileges (sudo).

If you have to add or uncomment those lines, you will need to restart ssh:

sudo /etc/init.d/ssh restart

Also verify the permissions of:

$HOME          drwxr-xr-x
$HOME/.ssh     drwx------

and the files contained in $HOME/.ssh :

authorized_keys and id_rsa    -rw-------
known_hosts                   -rw-r--r--

The rationale here is that openssh does not like if anyone else apart from yourself may have access to these sensitive files.

If you have to change the permissions. You may need to log out and in again for the changes to have effect.

---

