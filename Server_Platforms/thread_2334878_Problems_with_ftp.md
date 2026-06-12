---
title: "Problems with ftp"
date: 2016-08-23
forum: Server Platforms
---

### Post by kambiz2 on 2016-08-23
Hi,
I've got a problem with ftp and I can't guess where it is.
I've got Ubuntu 14.04 Server in my server. If I execute in the console
   ftp 127.0.0.1 it's ok
but if I execute with an external ip
   ftp 99.99.99.99 there is a problem, the error is: ftp: connect: No route to host.


If I try to connect via ftp, to the same external ip, from a Windows Pc, using Filezilla or directly command ftp, I connect without problems.

Can anybody tell me what I can do, test, ....
Thanks

To install ftp to the ubuntu server I executed this:
[COLOR=#000000][FONT=Arial]
sudo apt-get update[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get install vsftpd[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.bak  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo nano  /etc/vsftpd.conf[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]	[/FONT][/COLOR][COLOR=#000000][FONT=Arial]  [/FONT][/COLOR][COLOR=#999999][FONT=Arial]* *[/FONT][/COLOR]
[COLOR=#999999][FONT=Arial]*	*[/FONT][/COLOR][COLOR=#000000][FONT=Arial]write_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo service vsftpd stop[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo service vsftpd start[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by darkod on 2016-08-23
If the ftp is working from outside (from the internet), don't bother testing with the external IP from inside. If you have standard home router, some of them cannot route the traffic back immediately. Because when testing with the external IP from the local LAN, you are making the router send the traffic to itself, from the internal to the external interface and again the internal.

Test only from the outside and if it's working, great.

From the local LAN use the private LAN IP of the server and it should work also.

---

### Post by kambiz2 on 2016-08-23
Thanks darkod, the real problem I've got, is that I want to copy, via ftp, some folders to a remote pc, and the script throws the same error: No route to host.

The script I use is this:

#!/bin/bash


HOST="99.99.99.99"
USER="ftpuser"
PASS="password"
PORT="35"


# Call 1. Uses the ftp command with the -inv switches. 
#-i turns off interactive prompting. 
#-n Restrains FTP from attempting the auto-login feature. 
#-v enables verbose and progress. 


ftp -inv $HOST $PORT <<EOF
user $USER $PASS
cd /remotepath
put /home/myfolder/folderX/
bye
EOF

Sorry if there is a mistake. Now the server is turn off and I can't copy it, but more or less, this is the code

Thanks very much

---

### Post by darkod on 2016-08-23
I don't understand it... Can you connect with manual command from the machine where you want to run the script? Because if it works manually the script should work too.

Maybe you really don't have a route from that machine to the ftp destination...?

---

### Post by kambiz2 on 2016-08-28
darkod suggested me to use rsync instead of ftp to backup from ubuntu server to a remote windows computer.
After looking for information about rsync I've decided this configuration:

```
rsync -rtvu --delete /srv/samba/folderX user@remote_ip:/c/backup
```


After executing I've got this error:

```
ssh: connect to host 80.26.92.165 port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(226) [sender=3.1.0]
```

Internet says this error is because the remote folder doesn't exist. I'm new in all of this, but in this command I miss the password. Reading, I've seen to create a ssh public, and I've done:

```
$ ssh-keygen$ Enter passphrase (empty for no passphrase):
$ Enter same passphrase again:
```

After this the public key has been created in ~/.ssh/id_rsa.pub

Now, I should copy this key to the remote windows computer:

```
ssh-copy-id -i ~/.ssh/id_rsa.pub remote_ip
```

But, an other error appears:

```
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed/usr/bin/ssh-copy-id: ERROR: ssh: connect to host 80.26.92.165 port 22: Connection timed out
```

Any help please!!!
Thanks
[COLOR=#333333][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by darkod on 2016-08-28
Is the remote machine a linux with openssh-server installed?

First test ssh by doing:
```
ssh user@remote_ip
```

If it doesn't connect then ssh on the remote machine is not working correctly. In such case rsync will fail too because it depends on ssh.

You try to use /c/backup on the remote machine. Is that a windows?

---

### Post by kambiz2 on 2016-08-28
yes darkod, remote machine is a windows machine.
I think something is missing in the remote machine to be able to use rsync

Thanks

---

### Post by darkod on 2016-08-28
You need to install a SSH Server on the windows remote then. By default it doesn't include a ssh server so you can't connect to it remotely over ssh.

You have one tutorial here for example: [https://winscp.net/eng/docs/guide_windows_openssh_server](https://winscp.net/eng/docs/guide_windows_openssh_server)

You should be able to find many more if you search for a "ssh server for windows".

---

### Post by kambiz2 on 2016-08-28
Ok, that's ok. At the beginning, when you suggest better rsync than ftp, you told there was nothing to install in the remote machine. I couldn't understand how could be possible communication without installing ssh in windows machine, and I was trying looking for information.
I think I can't use rsync, because I haven't a remote machine, I've got a remote hard disk, it has it's own software to be use by ftp.
Anyway, it's difficult for me to explain it in english.
Thanks very much for your support

---

### Post by 1clue on 2016-08-28
ftp is extremely unfriendly to firewalls and to NAT (network address translation). The standard ftp server does not know how to handle traffic through a firewall, you need either pure-ftpd or something else specifically designed to work with firewalls.  And then you need cooperation from your firewall administrator, which you will probably not get if your server is in a corporate environment.

In my opinion FTP needs to become extinct.  It's extremely insecure by itself, and if there's a corporate firewall involved it causes the firewall to be insecure as well. If your home firewall is an out-of-the-box variety and has support for an ftp server on the inside then I recommend you not use that feature.

I strongly recommend sftp (based on ssh) or some other file sharing protocol, preferably with encryption built in.

---

### Post by kambiz2 on 2016-08-28
I believe both, and it's true there is a lot of information in internet, but it's true also, that it's not easy for beginners.
My environment is:
- ubuntu's server where there is the files to be copied
- a network hard disk, with is at the same time, smbserver, ftpserver and media server.

I can't install ssh server to the hard disk. 
With this environment which possibilites I've got and which is the best?

Thanks very much

---

### Post by darkod on 2016-08-28
> **kambiz2 said:**
> I believe both, and it's true there is a lot of information in internet, but it's true also, that it's not easy for beginners.
My environment is:
- ubuntu's server where there is the files to be copied
- a network hard disk, with is at the same time, smbserver, ftpserver and media server.

I can't install ssh server to the hard disk. 
With this environment which possibilites I've got and which is the best?

Thanks very much

Are the source and the destination in the same local network, or you will be connecting from source to destination over the internet?

---

### Post by kambiz2 on 2016-08-28
hi darkod, it'll be connected over internet, external ip, another network

---

### Post by darkod on 2016-08-28
In such case it is not very simple, especially if you are not experienced with these operations and with networking.

1. You started the thread by installing ftp server on the ubuntu server, but from what you explained now, you don't need ftp server on the ubuntu. The ftp server is on the destination, not the source. In this case your network HDD already has ftp server that you will be using.

2. You need to make sure you can reach your HDD ftp from the internet. If you can, it means you already have all the necessary setup. If you can't, you might need to do port forwarding and open port in the firewall on the router that you have in front of the network HDD.

3. After you have done step 2 successfully, you can start designing your script to do the copy to the ftp. Maybe this can help you, there are basic ftp commands that you can implement in a script according to your needs: [http://www.tldp.org/HOWTO/FTP-3.html](http://www.tldp.org/HOWTO/FTP-3.html)

---

### Post by 1clue on 2016-08-28
Can you tell us if the ftp server supports sftp?  This would be on port 22 by default.

---

### Post by darkod on 2016-08-28
> **1clue said:**
> Can you tell us if the ftp server supports sftp?  This would be on port 22 by default.

Yes, you can also check that.

It might not be necessary to "install" ssh on the network HDD, but most of those models allow you to "activate" ssh access. That means you will have rsync as available option as long as the network HDD accepts ssh. And it should.

And don't forget you might need to open and forward port 22 on the router that has the public IP.

---

### Post by 1clue on 2016-08-28
There are good reasons why I'm pushing ssh/sftp:
[LIST=1]
[*]It's much much easier to get working through a firewall, especially with NAT.
[*]It's secure.
[*]Having ftp open externally is an automatic fail for SOX compliance and several other certifications which may be in place at your remote site.
[*]It's probably already installed and possibly running on your remote host.
[*]It's much easier to convince your remote network's admin to open it.
[*]If you're married to the ftp command set, ssh/sftp supports that.
[/LIST]

---

### Post by kambiz2 on 2016-08-29
Hi darkod, at the beginning of this thread I was here, I can reach the remote hd via my own script, the problem I had was that I was not able to copy full folders, only files. For this reason I ask to the forum for some help.
The command mput of ftp only copies files.

Thanks

---

### Post by kambiz2 on 2016-08-29
Hi darkod, this disk doesn't support ssh, because it has some years. But I'm going to ask to by a new one, supporting ssh. Thanks

---

### Post by kambiz2 on 2016-08-29
Hi clue, I don't think so, but like I told in another post, I'll try to by another one

---

### Post by darkod on 2016-08-29
Yes, mput seems to copy only files.

There is additional program called ncftp that seems to allow to copy whole content of a folder (all files and subfolders). Check here: [http://www.cyberciti.biz/tips/linux-upload-the-files-and-directory-tree-to-remote-ftp-server.html](http://www.cyberciti.biz/tips/linux-upload-the-files-and-directory-tree-to-remote-ftp-server.html)

That should help you...

---

### Post by kambiz2 on 2016-08-30
Hi darkod, thanks for your information. This afternoon I'm going to install ncftp and try it.
I've been looking for a new network hard disk. I think WD MyCloud, supports SSH server, but I'm not sure. I've asked the confirmation. If it has, then we buy one. 

Thanks

---

