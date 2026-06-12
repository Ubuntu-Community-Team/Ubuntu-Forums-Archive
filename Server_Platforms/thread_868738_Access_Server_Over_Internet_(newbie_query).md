---
title: "Access Server Over Internet (newbie query)"
date: 2008-07-24
forum: Server Platforms
---

### Post by geomur on 2008-07-24
Hi Folks,

I have just got a LAN running with 8.04 server edition, getting out to the world via a network switch and a broadband cable modem.

I want to be able to a) access files on the server and b) stream webcam images, all from a remote computer.

I'm not even sure exactly what questions I need to ask to achieve this, but please could someone advise me how to start.

Many thanks

Geoff

---

### Post by wejick on 2008-07-24
very hard to understand your question. you must give us enough information coz i dont know about your server! "is it ftp server or nfs server or windows share"!

And stream your web cam! what kind of streaming, is it like youtube or yahoo messenger?

Sorry for my bad in english

---

### Post by Traumadog on 2008-07-24
> **geomur said:**
> Hi Folks,

I have just got a LAN running with 8.04 server edition, getting out to the world via a network switch and a broadband cable modem.

I want to be able to a) access files on the server and b) stream webcam images, all from a remote computer.

I'm not even sure exactly what questions I need to ask to achieve this, but please could someone advise me how to start.

Many thanks

Geoff

Hello Geoff,

I don't think I can help you with your streaming issues, however, I might be able to help with your wish to access files from remote locations.

First: You will need to make sure that you know the IP address that your ISP has assigned to you.  If you don't know that address, you can discover it by going to [http://www.ipaddressworld.com/](http://www.ipaddressworld.com/) . That site will return the IP address of the computer that contacted it. Next you should sign up with a dynamic DNS service such as DynDNS ([www.dyndns.com](www.dyndns.com)).  This is because most residential IP connections are "dynamic" and can change from time to time.  Services like DynDNS will help you track changes in your IP address so you don't have to constantly manually keep checking for changes.

Second: You should install an ssh server on your computer if you don't already have one.  OpenSSH is very popular and is available without cost.  (It may be in the Ubuntu Repositories, but I'm not sure on that.)  Once you have OpenSSH installed you can then use clients such as PuTTY for remote command line access to your server or WinSCP for remote file transfers.  The advantage of using SSH is that it is a reasonably secure method of connecting with your home server.  SSH (Secure Shell) encrypts your transmissions to and from the server and client.  After you have installed these software packages you will need to make sure any firewalls you have set up on your server and/or the router for your server will accept outside request for connections over port 22 or whatever port you select for your SSH communications.

That should get you started.

Hope this post was useful for you.  Let me know if you need further assistance.

Best Wishes,  :)

Traumadog.

P.S.  PuTTY can be downloaded from: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)  and WinSCP can be downloaded from: [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) .  Both are free of charge. :)

---

### Post by geomur on 2008-07-24
hi, thanks for replying.

The server is an apache2, samba, dhcp ubuntu 8.04.

The streaming is a webcam output to allow remote viewing.

Does that help...?

Best regards

geoff

---

### Post by ChumleyEX on 2008-07-24
Apache is what you want to use along with something for using the webcam. It will post the pictures from the webcam into your webserver folder so that you can view it. At that point you can even secure the folder that has the images in it. 

I'm sure there are craftier ways of going about this, but this is a good start.

---

### Post by silverglade00 on 2008-07-24
You can install ssh by going to the Terminal and typing

sudo apt-get install ssh denyhosts

That will get you everything needed. Denyhosts shuts people out when they fail at logging in too many times. You can leave it out if you want, but it's a good layer of security.

Don't forget to set your switch to forward port 20 to your server.

Sorry I can't help with the streaming webcam. You might want to try posting for some help in a non-server area to deal with that.

---

### Post by cariboo on 2008-07-24
If your webcam has a builtin web server you can access it through http. A freind of mine left his little web cam with me and it is attached to a very small device that has a built in web server. This one outputs to the ususal port 80, if you are the only person to access the webcan you can map it to a different port in your router.

Jim

---

### Post by thecircusb0y on 2008-07-24
a quick google revealed this ->: [http://streaming-webcam-ubuntu.qarchive.org/](http://streaming-webcam-ubuntu.qarchive.org/)

---

### Post by wejick on 2008-07-28
Hai thecircusb0y ithink there are many another good choice. You can try [webcam_server]("http://linux.softpedia.com/get/Communications/Conferencing/webcam-underscore-server-234.shtml")  but you need java enabled web browser to use it. 
If you want another method, you can use vlc. You can check this [link]("http://www.telscom.ch/index.php/downloads/streaming_from_webcam_with_vlc_on_linux").

---

