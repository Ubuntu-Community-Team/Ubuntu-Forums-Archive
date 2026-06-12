---
title: "MediaTomb"
date: 2010-07-28
forum: Server Platforms
---

### Post by 1serveyou on 2010-07-28
I'm trying to setup mediatomb so I can have it stream to my PS3, but I'm having a bit of a problem. I turned off the web user interface but when I put in the ip and port it still comes up. I remember reading that this allows anyone to get into your files and download them which I don't want. Thanks in advance!

---

### Post by CharlesA on 2010-07-28
It will only allow UPNP devices on your local network to access files.

Do you have a firewall enabled that would be blocking the port it uses for the web interface?

---

### Post by arrrghhh on 2010-07-28
Ok, I know I probably should just try to help with Mediatomb...

But unless it's changed drastically (doubtful) I would highly recommend [PS3 Media Server](http://code.google.com/p/ps3mediaserver/) over it.  Works worlds better than Mediatomb (espeically for the PS3, since that's what it is built for) and is a heckuva lot easier to setup.  It's not in the repo's, but there's a few places that host new files if you don't mind modding your sources.list.

With that said, it will allow ANY UPNP capable device to connect - however, this only applies to your LAN - so only devices on your local network.  Also, the webui doesn't really allow people to 'download' your files... It just is for managing Mediatomb.  If you turn it off, you can't manage it any longer.  If you want it blocked to the outside world, your router should do that.  If you don't have a router, you better have a firewall running on that machine!  UFW is the easiest to use.  You could just block the port with UFW as well, but again you would have to unblock that port to manage Mediatomb.

---

### Post by CharlesA on 2010-07-28
+1 for PS3 Media Server.

I used it, but my server choked on doing transcoding on-the-fly.

Worked well for anything that didn't need to be transcoded tho. :)

---

### Post by 1serveyou on 2010-07-28
Thanks guys. 
 
Arrr - How would I get it into my source list, and will I have any problems running it on 9.04?

---

### Post by CharlesA on 2010-07-28
You don't add it to the sources.list file.

Just download it, unzip and run.

---

### Post by 1serveyou on 2010-07-28
> **CharlesA said:**
> You don't add it to the sources.list file.

Just download it, unzip and run.

When I try to run it, it says "Java not found." I tried to install Java but it kept on saying there was an error.

*edit -  I had to download the "ubuntu restricted files" file, and now it seems to work, although a bunch of HD things stutter.

---

### Post by jbrown96 on 2010-07-28
I don't like PS3mediaserver at all. There's no way to disable transcoding on the host, so it uses a lot of CPU. It also has way more dependencies and there's no Ubuntu package, so it can be a challenge to get working correctly.
Mediatomb uses practically zero system resources and is usually dead simple to configure. 

It would be helpful to know your network topology (i.e. tell us about your modem, router, port forwarding if you configured it, and IP of your Ubuntu box), then I can show you to use mediatomb.

As long as you haven't configured port forwarding, there's no security risk from the outside world.

My mediatomb server is directly connected to the network, so I restrict it to listening on a single port. Here's my command ```
mediatomb -a 10.0.0.1 --daemon
``` I'm using a 10.0.0.0/28 local network.


Edit:
You can also setup a firewall simply. ```
sudo ufw enable
 sudo ufw allow 1900/tcp
 sudo ufw allow 1900/udp

``` that will allow playing content on your PS3 but block the web interface.
If you are using anything except some obscure DSL vendors or a cable modem connected directly to your computer, which is very unlikely since you have a PS3 on the network, this is a complete non-issue. You would have to configure your router to allow port 49152 from the internet to your Ubuntu box, and you would know if you had done this. I wouldn't worry about it.

---

### Post by CharlesA on 2010-07-28
> **1serveyou said:**
> When I try to run it, it says "Java not found." I tried to install Java but it kept on saying there was an error.

*edit -  I had to download the "ubuntu restricted files" file, and now it seems to work, although a bunch of HD things stutter.

Yeah, the restricted extras probably had the java dependencies you needed.

This is how I installed it on my machine: [http://ubuntuforums.org/showpost.php?p=9486521&postcount=6](http://ubuntuforums.org/showpost.php?p=9486521&postcount=6)

---

### Post by arrrghhh on 2010-07-29
Wow.  So you don't *have* to add it to your sources, but then you get new updates without fuss.  You can also turn off transcoding, in fact my issue with Mediatomb was compatibility... a TON of files would not work, and one way or another I can get PS3MediaServer to play pretty much everything.

Check out [this](http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=5589) post if you want to add it to your sources.list.

And I swear you can disable the transcode feature if you really want to... but in my experience the PS3 is very picky in what it will play, and the transcoding feature is very resource hungry... but totally worth it IMHO.
If you do want to transcode (which is important to me) you may want to run it with a gui.  Just forward X across SSH and when you restart the service you'll get a window - here is where you can control all the settings normally configured thru the configuration file.

If you fiddle with the settings (and are on a high speed network with a *fairly* beefy server...) you should be able to transcode HD.  My server will do 720p no problem, but starts choking on 1080.  I'm told you need a quad-core proc to do 1080.  I have a cheapo dual-core, and like I said it does 720p... But I had to adjust the buffer settings and get all the little pieces working correctly.

---

### Post by 1serveyou on 2010-07-29
I'll report back more but this is what I was talking about with the interface

[http://mediatomb.cc/pages/documentation](http://mediatomb.cc/pages/documentation)

> **WARNING! **

The server has an integrated filesystem browser,  that means that anyone who has access to the UI can browse your  filesystem (with user permissions under which the server is running) and  also download your data! If you want maximum security - disable the UI  completely! Account authentication offers simple protection that might  hold back your kids, but it is not secure enough for use in an untrusted  environment!
Note:since  the server is meant to be used in a home LAN environment the UI is  enabled by default and accounts are deactivated, thus allowing anyone on  your network to connect to the user interface.



---

### Post by arrrghhh on 2010-07-29
Eek.  Yet another reason to avoid it :P

It was a great piece of software, don't get me wrong... it just seems like the development has slowed to beyond a crawl.

Use what works for you tho, I've always been a firm believer in that.  Just want to highlight alternatives!

---

