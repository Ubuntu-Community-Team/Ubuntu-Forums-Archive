---
title: "Howto setup ssh access to Ubuntu from Windows bash, Android and iOS/iPad"
date: 2017-02-13
forum: Tutorials
---

### Post by fboecom on 2017-02-13
**[SIZE=3]Intended audience[/SIZE]**

This guide is for owners of a private Ubuntu server who want to access it safely from any usual client, including Windows10 bash, Windows PuTTY, Filezilla, Ubuntu, Android, iPad and the iOS like.
Basic documentation: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) 
Good reading: [https://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login](https://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login)
More on security is here: [https://askubuntu.com/questions/2271/how-to-harden-an-ssh-server](https://askubuntu.com/questions/2271/how-to-harden-an-ssh-server)
 
[SIZE=3]**Installing SSH and creating pairs**[/SIZE]

Assuming you start from an Ubuntu client, creating a private and public pair where the public one is for use on your Ubuntu server.

open terminal (in home directory)
 
*(any unbuntu, if needed)*
```
sudo apt-get update
```
 
*(in Ubuntu bash Windows10)*
Yes, it is off-topic, but nevertheless (*we want to honour Msoft's bow to Ubuntu won't we*), the first time you will encounter an error on sudo (while it *will* work):
> cannot resolve hostname..
*(if needed type)*
```
hostname
```
*(make then hostname known to the hosts file)*
```
sudo nano /etc/hosts
```
add a newline with
```
127.0.0.1 <hostname>
```
The <hostname> in this case is the Ubuntu bash/Windows10 client's name.
 
*(any ubuntu if needed)*
```
sudo apt-get install openssh-server
```
*(all ubuntu then)*
```
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa
```
 
system responds:
```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/b/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/b/.ssh/id_rsa.
Your public key has been saved in /home/b/.ssh/id_rsa.pub.
```
 
For the passphrase you need a strong password/phrase.
[https://help.ubuntu.com/community/StrongPasswords](https://help.ubuntu.com/community/StrongPasswords)
 
in .ssh are now 2 files:
1.       id_rsa (private key)
2.       id_rsa.pub (public key)

[SIZE=3]**Installing public key in your server**[/SIZE]
For most of the text below, the <host> is in fact the server you want to access with one of your clients.
The key you need to transfer to the server/host is the public one. If you can log in to a computer over SSH using a password, you can transfer your RSA key by doing the following from your own computer:
Later in this guide I would propose to change the ssh port number on the server, but for now lets assume or leave it at 22.
```
ssh-copy-id <username>@<host>
```
Where <username> and <host> should be replaced by your username and the name of the computer you're transferring your key to.
If the port on the server is different than 22, you can:
```
ssh-copy-id "<username>@<host> -p <port_nr>"
```.
Another alternative is to copy the public key file to the server and concatenate it onto the authorized_keys file manually. It is wise to back that up first:
```
cp authorized_keys authorized_keys_Backup
cat id_rsa.pub >> authorized_keys
```
 
You can make sure this worked by doing:
```
ssh <username>@<host>
```
 
commands and replies:
```
<hostname-dir>:~/.ssh$ ssh-copy-id <user>@<host>
The authenticity of host 'x.x.x.x (<host>)' can't be established.
ECDSA key fingerprint is 77:9c:60:18:ac:01:e4:54:a7:41:8b:b7:89:bd:e2:8c.
Are you sure you want to continue connecting (yes/no)? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
<user>@<host>'s password:
 
Number of key(s) added: 1
 
Now try logging into the machine, with:   ssh '<user>@<host>'
and check to make sure that only the key(s) you wanted were added.
if your server has another port assigned to ssh, use the command ssh -p <portnumber> <user>@<host>
```
 
[SIZE=3]**Enhancing security**[/SIZE]
On the host/server, assuming you can still login there with a password, or directly on a console, you would like to disable passwords for ssh. Further you would change the port number, check the several security topics, it adds to safety or at least reduces the many rejected login attempts in auth.log files. 
 
```
sudo nano /etc/ssh/sshd_config
```

Set the following settings to the following values.
If these settings are already in the file, set them to "no" rather than add new lines.
```
Port <new port number>
ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no
```
Once this is done, restart the SSH daemon to apply the settings:
```
sudo service ssh restart
```
 Make sure you now use the new port number in all client settings below.

[SIZE=3]**Moving the private key to an accessible but private location**[/SIZE]
The host / server only holds the public key, not the private key. In all of the text below, distributing a key means distributing the private key.
 
So, from where you have created the pair, and have your private key (in the ~/.ssh directory), you want to distribute the private key to some devices you are using. 
First, make sure you store the key in a secure and accessible cloud location, that only you can access.
I would use onedrive or dropbox, as you can up and download from there into unix or tablets quite easily. So from your Ubuntu client you would need to copy the file id_rsa from ~/.ssh, maybe in a few steps, to dropbox or onedrive.
 
If you were using Ubuntu bash on W10 while creating the pair, then the location of your ssh key file is at:
```
C:\Users\<USERNAME>\AppData\Local\Lxss\home\<USERNAME>
```

[SIZE=3]**Enabling several clients.**[/SIZE]

**Other Ubuntu**
[INDENT]that's plain simple, if needed install openssh-server and create another .ssh folder in the client's home directory.
Copy the id_rsa in some way (downloading from a onedrive or dropbox website) and copy it to the ~/.ssh folder.
Most probably you will have to do:
```
cd ~/.ssh
chmod 700 id_rsa
```[/INDENT]
**Windows 10 - Putty**
[INDENT]Download if needed the file id_rsa on onedrive or dropbox to your client machine.
Get the product puttygen, such as available in Winscp [https://winscp.net/eng/download.php](https://winscp.net/eng/download.php); kick that program off, select conversion, import key id_rsa from onedrive, dropbox or the Appdata location if its the same machine as the Ubuntu bash is on.
A ppk key will be generated. Store it, also handy on onedrive or dropbox.
Open PuTTY with that new .ppk file specifying it in the SSH settings section. [/INDENT]
**Windows 10 and Ubuntu Filezilla ftp**
[INDENT]Will not work with a passphrase key, official instruction is:
*In the Edit - Settings menu of the FileZilla client, you can [Add key file...] under Connection - SFTP, and FileZilla can then use the public key authentication in the site manager with the 'Interactive' Logontype on connection. Note: Importing a site's public key is not supported.*
The process is working well. you create a non-password key and again that one you can store on onedrive or dropbox to use on all your Filezilla clients.[/INDENT]
**Android**
[INDENT]Download your id_rsa file with a tool like ES file explorer to your device, either with onedrive, dropbox, accessing a mapped drive or even by sd card. 
Save the file for instance in /storage./emulated/0/Download (a*s the app such as Termius will find it there. I am mentioning Termius because it was working&easy. Other ssh solutions will exist*).
Then go to Playstore- install Termius - click on plus sign, new host nickname, real name or ip address, check ssh, specify port, user, click on key, on the plus sign import key or paste from the pasteboard. Searching will find the key. 
Saving with the V check mark and going back and you're done.[/INDENT]
**iOS / iPad / iPhone**
[INDENT]For iPad, install Shelly from the Appstore (*will cost you Eur3,99 for the ssh keys feature; I am mentioning Shelly because it was working&easy. Other ssh solutions will exist.*), specify the user@ip address and port. Then (switch to onedrive, browse to the folder where id_rsa is stored, tap it , add to dropbox (onedrive cannot open the text file!!)) and/or go straight to dropbox if you saved it there, click/  tap it, it will open as text, select all, copy. Switch back to Shelly, click Settings, click Key file, Import key from pasteboard, enter the Passphrase, click Import, click Done. Termius will probably work fine too, it works on iPhone (Shelly does not) but it is more confusing to configure than on Android.[/INDENT]
**Alternative key processing**
[INDENT]Some Apps will allow or even require that they create their own private-public pair. That makes the private key handling easy (done by the app) but then you have to add the public key to your server. After generation, the app should allow you to save or send the public key. When by email, you can simply copy the text starting with 'ssh-rsa' up till the end, and save it in your server's ~/.ssh directory, and then, say the name of the file you created is 'app.pub':
```
cat ~/.ssh/app.pub >> ~/.ssh/authorized_keys
```
[/INDENT]

Open up your router's configuration, Advanced settings and Portforward your (required fixed) internal IP address and port to the Internet - and enjoy your totally secure ssh access from anywhere on the globe with any device.
Tunneling vnc over ssh will superbly add to the fun. Do not forget to add -localhost to your vncserver statement and add 127.0.0.1 to your app's vnc hostname to be using the very secure vnc over ssh.

---

