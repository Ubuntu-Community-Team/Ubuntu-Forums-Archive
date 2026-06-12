---
title: "SFTP with Dynamic IP"
date: 2011-03-18
forum: Server Platforms
---

### Post by 4eva on 2011-03-18
Hi,

I would like to setup SFTP file server but I have dynamic ip. I have zero knowledge about this. I already have openssh running and I am able connect to the "file server" using putty for now.

Guides would be useful.

Thank you. :confused:

---

### Post by hawk2010 on 2011-03-18
I think you may use dyndns to and use the domain since the dynamic IP tracking will be done by DynDNS.  Otherwise you have to a script which check's your external IP and mail you that when changed.

---

### Post by BkkBonanza on 2011-03-18
Sign up for a free DynDns or NoIp account to get a domain name.
Install **ddns3-client** package and config to update your account with your username and pwd.
This program will update your domain name when your dynamic IP changes.

(Not just DynDns and NoIp support but many other services too)

Note - if you have a router between your server on the internet then first check if it has DynamicDNS built in as it's easier just to set the user/pwd values there and let it do this.

---

### Post by lisati on 2011-03-18
+1 for using a service like DynDns or no-ip to help manage a domain name. If you're in luck, you might be able to configure your router to do the updates for you, without the need for downloading the relevant client.

---

### Post by 4eva on 2011-03-19
> **hawk2010 said:**
> I think you may use dyndns to and use the domain since the dynamic IP tracking will be done by DynDNS.  Otherwise you have to a script which check's your external IP and mail you that when changed.

> **BkkBonanza said:**
> Sign up for a free DynDns or NoIp account to get a domain name.
Install **ddns3-client** package and config to update your account with your username and pwd.
This program will update your domain name when your dynamic IP changes.

(Not just DynDns and NoIp support but many other services too)

Note - if you have a router between your server on the internet then  first check if it has DynamicDNS built in as it's easier just to set the  user/pwd values there and let it do this.

> **lisati said:**
> +1 for using a service like DynDns or no-ip to  help manage a domain name. If you're in luck, you might be able to  configure your router to do the updates for you, without the need for  downloading the relevant client.


Yup, my router does support it dynamicdns. :)

Do any of you have a guide to set-up this kind of server ? :popcorn:

---

### Post by BkkBonanza on 2011-03-19
It depends on what you want. If the ssh server is running then basically that's all you need to have an sftp server. Any sftp client can connect to it and do sftp commands to work with files. eg. Nautilus has sftp built in so it can connect with user/pwd and see the files natively. Same with other sftp clients.

However, if you're thinking of having public access or specific user access then you would want to configure a bit further to manage access restrictions, permissions etc. So it depends on your goals here.

---

### Post by 4eva on 2011-03-19
> **BkkBonanza said:**
> It depends on what you want. If the ssh server is running then basically that's all you need to have an sftp server. Any sftp client can connect to it and do sftp commands to work with files. eg. Nautilus has sftp built in so it can connect with user/pwd and see the files natively. Same with other sftp clients.

However, if you're thinking of having public access or specific user access then you would want to configure a bit further to manage access restrictions, permissions etc. So it depends on your goals here.

Oh okay I would search over the forum for some guide. Thanks :)

---

### Post by papibe on 2011-03-19
This is a [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

I hope it helps.

---

### Post by 4eva on 2011-03-20
> **papibe said:**
> This is a [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

I hope it helps.

Thank you that was a very useful information. Now I have to set-up the file server for that. :popcorn:

---

### Post by 4eva on 2011-03-20
> **4eva said:**
> Thank you that was a very useful information. Now I have to set-up the file server for that. :popcorn:

I tired finding guide to set-up ftp server for this but I could no find it. Any chances that anyone of you have a link for this ? :frown:

---

### Post by papibe on 2011-03-20
> **4eva said:**
> set-up ftp server frown:
You don't have to. If you install OpenSSH you can use sftp, which is a lot more secure than ftp.

There are general steps.
[INDENT][LIST=1]
[*]Install the package openssh-server.
[*]Change the de default port from 22 to something different (like 2222) [not mandatory but higly recommended].
[*]Forward the port in the router to your server.
[*]Go outside your home network to test it (like an internet cafe).
[/LIST][/INDENT]

As for the client side, it depends what OS you'll use. On Ubuntu you can use the terminal, or a graphical interface like Filezilla. On Windows you can also use Filezilla or WinSCP (which I recommend).

Another way would be use the FireFTP addon for Firefox, which would work on any underlying OS.

I hope it helps.

---

### Post by BkkBonanza on 2011-03-21
You still have not indicated what you actually want.

Do you want an sftp or an ftp server? They are different things.

Do you want to have just access for yourself and a limited few users or do you want public access, anonymous public access? All things affect what you should choose to do and how.

I tried to indicate that earlier but you're running off looking for guides without having explained what you want. There are thousands of various ftp or sftp tutorials out there to find on Google. But if you don't know what you want you'll just be confused by them.

---

### Post by 4eva on 2011-03-21
> **papibe said:**
> You don't have to. If you install OpenSSH you can use sftp, which is a lot more secure than ftp.

There are general steps.[INDENT]
[LIST=1]
[*]Install the package openssh-server.
[*]Change the de default port from 22 to something different (like 2222) [not mandatory but higly recommended].
[*]Forward the port in the router to your server.
[*]Go outside your home network to test it (like an internet cafe).
[/LIST]
[/INDENT]As for the client side, it depends what OS you'll use. On Ubuntu you can use the terminal, or a graphical interface like Filezilla. On Windows you can also use Filezilla or WinSCP (which I recommend).

Another way would be use the FireFTP addon for Firefox, which would work on any underlying OS.

I hope it helps.

Thanks for the reply ! Will try this but need to get my hands on an outside connection. :KS

> **BkkBonanza said:**
> You still have not indicated what you actually want.

Do you want an sftp or an ftp server? They are different things.

Do you want to have just access for yourself and a limited few users or do you want public access, anonymous public access? All things affect what you should choose to do and how.

I tried to indicate that earlier but you're running off looking for guides without having explained what you want. There are thousands of various ftp or sftp tutorials out there to find on Google. But if you don't know what you want you'll just be confused by them.

Oh... I want to setup a file server which I can access file remotely if possible map as a network drive. Using any kind of method would be fine for me.

I have finished solved the dynamic ip problem for "server" using dyndns.

---

### Post by BkkBonanza on 2011-03-21
In that case you should use sftp not ftp. sftp is available natively in SSH, so if you have sshd-server installed on the server and can login using ssh then you already have full sftp available.

How you use it depends on the OS you access from. If Ubuntu then just use Nautilus as it has sftp built in. If on Windows then a good client is WinSCP (available free). Just install it as usual and then use it to connect to your server (which again goes over ssh).

In Nautilus you simply enter a location (or use the menu, Places, Connect to Server). The location follows the format of:

sftp://user@server:/path/to/directory

eg.
sftp://joe@myhome.dyndns.com:/home/joe

You can add a bookmark for this once you are connected so that future connects are one-click easy.

It will prompt for a password when connecting. If you want it more seamless then you can create a key and setup for key authentication. There are many tutorials around for that and the simplest method involves using **ssh-copy-id** from your client machine (assuming using linux here) to copy your key to the server to allow access. Once using a key you can access securely without password as Nautilus knows how to provide the key to the server during connection.

To go further and mount a remote directory on your machine you would be looking for a guide on installing and using **sshfs**. This is a fuse based filesystem that uses ssh and sftp commands to make a remote directory appear as mounted locally. It works well but is a few more steps to configure.

---

### Post by 4eva on 2011-03-21
> **BkkBonanza said:**
> In that case you should use sftp not ftp. sftp is available natively in SSH, so if you have sshd-server installed on the server and can login using ssh then you already have full sftp available.

How you use it depends on the OS you access from. If Ubuntu then just use Nautilus as it has sftp built in. If on Windows then a good client is WinSCP (available free). Just install it as usual and then use it to connect to your server (which again goes over ssh).

In Nautilus you simply enter a location (or use the menu, Places, Connect to Server). The location follows the format of:

sftp://user@server:/path/to/directory

eg.
sftp://joe@myhome.dyndns.com:/home/joe

You can add a bookmark for this once you are connected so that future connects are one-click easy.

It will prompt for a password when connecting. If you want it more seamless then you can create a key and setup for key authentication. There are many tutorials around for that and the simplest method involves using **ssh-copy-id** from your client machine (assuming using linux here) to copy your key to the server to allow access. Once using a key you can access securely without password as Nautilus knows how to provide the key to the server during connection.

To go further and mount a remote directory on your machine you would be looking for a guide on installing and using **sshfs**. This is a fuse based filesystem that uses ssh and sftp commands to make a remote directory appear as mounted locally. It works well but is a few more steps to configure.

Oh thank you, it worked ! :D

Well now I want to go a little bit further. Is it possible to set-up account for a user and only enabling him/her to access only that folder ? :o

---

### Post by BkkBonanza on 2011-03-21
It is possible to do that. I haven't done it myself but I googled and found the steps for you. See this tutorial below, which appears good for Ubuntu.

[http://linuxdocument.blogspot.com/2010/01/how-to-restrict-ssh-sftp-user-only.html](http://linuxdocument.blogspot.com/2010/01/how-to-restrict-ssh-sftp-user-only.html)

Basic outline:

1. Modify sshd_config to use internal sftp and add restrictions.
2. Add new group eg. sftponly.
3. Add new user and make them member of that group.
4. Create the home for that user which must be owned/writeable only by root.
5. Try logging in with that user to ensure it works.

---

### Post by 4eva on 2011-03-22
> **BkkBonanza said:**
> It is possible to do that. I haven't done it myself but I googled and found the steps for you. See this tutorial below, which appears good for Ubuntu.

[http://linuxdocument.blogspot.com/2010/01/how-to-restrict-ssh-sftp-user-only.html](http://linuxdocument.blogspot.com/2010/01/how-to-restrict-ssh-sftp-user-only.html)

Basic outline:

1. Modify sshd_config to use internal sftp and add restrictions.
2. Add new group eg. sftponly.
3. Add new user and make them member of that group.
4. Create the home for that user which must be owned/writeable only by root.
5. Try logging in with that user to ensure it works.

Hi,

I tried [http://solderintheveins.co.uk/2011/03/ubuntu-sftp-only-account-how-to/](http://solderintheveins.co.uk/2011/03/ubuntu-sftp-only-account-how-to/) instead but whenever I use another pc to connect to the server, a .cache automatically created. Is there anyway to solve this ?

Thanks.

:)

---

### Post by BkkBonanza on 2011-03-22
That looks like a great tutorial. 
I'm not sure what you mean by .cache created though.

---

### Post by 4eva on 2011-03-22
> **BkkBonanza said:**
> That looks like a great tutorial. 
I'm not sure what you mean by .cache created though.

Opps... I mean a folder ".cache" is automatically created whenever I log on. :popcorn:

---

