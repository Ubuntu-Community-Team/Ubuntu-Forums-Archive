---
title: "Streaming media from server...."
date: 2009-04-02
forum: Server Platforms
---

### Post by mramsey on 2009-04-02
I have searched but not found what I am looking for. I have just configured my Ubuntu server with the usual stuff (shares, printers etc) Now I want to do something else with it. I want to be able to stream my mp3 files not only inside of my network but outside as well. A web interface would be ideal but an installed application would work as well on the client machine. Needs to support M$ Windows and Ubuntu. Any input is appreciated.

---

### Post by HermanAB on 2009-04-02
The super easy way to stream audio is with Edna.  I have been using it for years.  See the bottom of this page:
[http://aeronetworks.ca/ogg2mp3-howto.html](http://aeronetworks.ca/ogg2mp3-howto.html)

---

### Post by dmitriyp13 on 2009-04-02
If you dont mind spending a little bit of time, Jinzora seems like the perfect solution.  It requires a web server, php and MySQL but it looks fairly staightforward to setup.  There's a good guide to getting it up and running here ([http://lifehacker.com/software/home-server/geek-to-live-build-an-internet-jukebox-with-jinzora-254178.php](http://lifehacker.com/software/home-server/geek-to-live-build-an-internet-jukebox-with-jinzora-254178.php)).  Once you have it set up, playing music works through a web browser and can be done on Windows, Linux or Mac.

---

### Post by volkswagner on 2009-04-03
+ 1 for Jinzora.  The above link is for windows install.  The program is way cool.  You will need to modify your php config to boost some setting above the default.

It looks like they have been doing some site updates.  Finding the download is not hard, but install directions are missing at the moment.  They are still avail. on the [wiki]("http://en.jinzorahelp.com/wiki/Linux_Installation_with_shell_access").

The biggest con is lack of support.  There is a forum, but little action, and not moderated by the original coders.

I still highly recommend it since I have yet to find anything better.  One cool function is ability to play back locally.  If your server had speakers or was connected to your home stereo, you can select Jukebox mode in the config.  When playing back in any web browser you can select Jukebox rather than stream....so cool.

Words to the wise.  If you want the protection for using login with passwords, don't enable the anonymous user.  It is hard to undo without reinstall, which is really easy.  I think it is a bug, not sure if it was fixed in the 2.8 release.

---

### Post by mramsey on 2009-04-04
Thanks for the info... Jinzora looks to be what I am after!:p

---

### Post by JohnnyVW on 2009-04-04
Yet another +1 for Jinzora!

Like volkswagner said, there isn't a huge support base.  If more are using it, that could get better.

The Anonymous issue is still present in 2.8.  I also had to re-install to get rid of it...

Some other useful links:

[**How To Install And Setup Jinzora Media Server In Ubuntu**](http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25)

[**How-To: Ubuntu Media server**](http://rubbervir.us/projects/ubuntu_media_server/part2.html)

I just have it set up on our local network.  We have an old Latitude CPX-J in the bedroom that is used as a 'Net Radio (streaming radio, mp3, CD's, etc.).  With this setup, I can put all of my wife and my CD's and talk shows on the Jinzora server and listen in the bedroom, or wherever.

All in all, we both really dig it.  Neat program!

---

### Post by mramsey on 2009-04-12
Wow! I love it. Jinzora has everything I was looking for. The installation was pretty straight forward. =D>

---

### Post by hyper_ch on 2009-04-12
I used gnump3d this far. Very simple and easy to use :)

---

