---
title: "How to allow Windows person access to server"
date: 2008-08-14
forum: Server Platforms
---

### Post by hrod beraht on 2008-08-14
What's the preferred way to allow a Windows user access to the /var/www folder on a LAMP server so that they can place .html files there easily over the LAN.

I use SSH from my Ubuntu box, and suppose the Windows person could use PuTTY, but that might be a training nightmare.

Is there a good way to give them drag-and-drop access? SAMBA? Or something else I'm not thinking of? Personally, I can't imagine using anything other than SSH, and I've used SSH for so long that this is actually puzzling me :D

Bob

---

### Post by windependence on 2008-08-15
Best way is with WinSCP. 

-Tim

---

### Post by hrod beraht on 2008-08-15
Actually, WinSCP is a great idea. And there is even a [[COLOR="Blue"]portable version[/COLOR]]("http://portableapps.com/apps/internet/winscp_portable") of it!

Bob

---

### Post by Krupski on 2008-08-18
> **windependence said:**
> Best way is with WinSCP. 

-Tim

THIS ([**[COLOR="Blue"]LINK[/COLOR]**]("http://www.bitvise.com/tunnelier")) is also a great Windows SSH client. It has graphical drag-n-drop SFTP and a terminal console... both of which are SSH secure.

Oh... it's also free!

-- Roger

---

### Post by HermanAB on 2008-08-18
Filezilla is likely the easiest FTP/SFTP client for windoze.

Cheers,

Herman

---

### Post by moonpup on 2008-08-18
quick question regarding filezilla... does it support public key authentication like winscp? If it does, where is the option for it as i have never seen it :)

---

### Post by Kolipoki on 2008-08-18
> **windependence said:**
> Best way is with WinSCP. 

-Tim

Second that... It also lets you edit files and can perform the tar/untar functions and much more. No FTP server. Sweet...

---

### Post by HermanAB on 2008-08-18
Filezilla key authentication:
[http://wiki.filezilla-project.org/Howto](http://wiki.filezilla-project.org/Howto)

For SFTP using SSH2, FileZilla utilizes the excellent PuTTY tools. To allow the use of RSA / DSA key files with Filezilla, you'll need to download two more tools from PuTTY: Pageant and (assuming your key file isn't already in PPK format) PuTTYgen.

If your key file is already in PuTTY's PPK format you can skip this paragraph. However if your key is in OpenSSH format, you first need to convert it to PuTTY's PPK format. To do this, launch PuTTYgen and from the "Conversions" menu, select the "Import key" option. Select your key and follow the prompts to enter your pass phrase. Save your private key.

Now run Pageant. In your system tray, you'll see the Pageant icon appear. Right-click the icon and select "Add Key" and select your private key (PPK) file. Follow the prompt to enter your pass phrase and you're done.

Now simply launch FileZilla and connect to your server using SFTP using SSH2 with a username and an empty password. Don't forget to close pageant when you're done.

I'm not sure how well this'll work on systems where you're forced to not save your password, but after selecting "Don't save password" in the site manager for my server, I could exit the site manager by pressing "cancel" on the password dialog and then "Save and Exit". When you select your site from the list, again press "cancel" and it'll still attempt to connect.

As you may or may not know, FileZilla can be easily carried around on portable media such as a USB stick and used from any PC. This also applies to the PuTTY tools, so if you stick Pageant and your PPK key file on to, for example, a USB stick, you can now access your server from any Windows PC.
[edit] Alternative Method

In the Edit - Settings menu, you can [Add key file...] under Connection - SFTP, and FileZilla can use the public key authentication in the site manager with the 'Interactive' Logontype. However, the .ppk file is converted to unprotected one if the original .ppk file is password-protected (FileZilla can do that for you when importing the file). As of 3.0.10, a password-protected key file is not supported yet.

---

### Post by moonpup on 2008-08-18
Thanks for the info :) I was hoping it was built in like WinSCP, but that's cool at least I now know that it's possible although it takes a few extra steps.

---

