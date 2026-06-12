---
title: "Can't access thumb drives or DVD drive"
date: 2013-11-15
forum: Virtualisation
---

### Post by Tom_ZeCat on 2013-11-15
Previously I was able to access everything.  They stopped working after I did a search of my hard drive in Kubuntu to delete unneeded ISO files.  I download videos and burn them to DVD via DeVeDe.  The first step is always to make an ISO file.  I used a search program to search and find these ISOs and delete them.  I thought I only deleted ISOs that I no longer needed.  Maybe not.  

Now when I turn on VirtualBox I get an error message saying that one or more device isn't accessible (screenshot below).  I'm able to start up Windows 7 under VB and I can run software installed to it.  I just can't access any drives other than its virtual C drive.  In VB I've made sure to add the filters.  

I guess I could uninstall and reinstall, but it would be nice if I could just fix this so I didn't have to get that drastic.  Perhaps you can tell what's happening via the screen shot

[IMG]http://imageshack.us/photo/my-images/42/uuw.gif[/IMG]

Screen shot doesn't appear to be hot linking.  Here's a direct link: 
[deleted]
Edit: Trying a different one:
[http://imageshack.us/photo/my-images/32/q9q.gif/]("http://imageshack.us/photo/my-images/32/q9q.gif/")
(When you click on the link, it will pull up the screen shot, but you need to click on the icon that looks like a magnifying glass to see it full size.

---

### Post by bashiergui on 2013-11-23
Download and install the latest version of VB and the guest additions. Check the vm settings that the usb and cd drives are set to pass through.

---

