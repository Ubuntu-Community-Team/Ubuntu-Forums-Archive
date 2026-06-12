---
title: "home web server - sharing images or video questions"
date: 2009-03-25
forum: Server Platforms
---

### Post by theRick on 2009-03-25
I have been playing around with an ubuntu server sitting headless in my spare bedroom and have it setup as both a LAMP and an internal samba server.

I also have Dyndns setup so I can easily access outside home.

My question is, is there any type of web software that I could install where basically it would display all images in a directory in a nice display or one that would make it really easy to display a list of video files so a family member (accessing via the internet) could stream it or download it.

Obviously I'd want some security on it so not just anyone could view it, but I want to keep it as simple as possible for my family members to access who are not computer savvy and something where all I need to do is drag and drop my files into the appropriate internal network folder.

Anything like this exist?

---

### Post by sammy_pal on 2009-03-26
Have a look at this - [http://packages.ubuntu.com/intrepid/web/album](http://packages.ubuntu.com/intrepid/web/album)

Regarding streaming media files, you can try gnump3d - [http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)
It can stream audio and video files.

For security you can use the password authentication in Apache using .htaccess file, which is one of the most simple and reasonably secure method. Here is a howto on this - [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

Hope this helps.

---

