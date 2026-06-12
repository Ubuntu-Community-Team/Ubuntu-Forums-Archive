---
title: "Apparmor-enforce on Firefox prevents it from running"
date: 2014-11-07
forum: Security
---

### Post by jamal5 on 2014-11-07
On a fresh install of Ubuntu I set up apparmor to enforce on Firefox. With this restriction, upon trying to start up Firefox, I would get the message "input/output error" and it wouldn't start up.

I changed the mode to complain and it began working just fine. I feel that it's very important to restrict Firefox for security, and the complain mode obviously doesn't mean much... Is this a common issue and is there some way to fix it? I rather not have to switch to selinux...

The only commands I ran were   sudo apt-get apparmor-utils   sudo aa-genprof firefox    sudo aa-enforce firefox         

Thanks

---

### Post by TheFu on 2014-11-07
[http://www.youtube.com/watch?v=2x8_76rFcM4](http://www.youtube.com/watch?v=2x8_76rFcM4)
might help.  I've never done this, but it seems really easy.

SELinux is impressive. If you think you need it, I would encourage the use, but don't expect it to be _easier_ than apparmor.

---

### Post by vasa1 on 2014-11-07
> **jamal5 said:**
> ...
The only commands I ran were   sudo apt-get apparmor-utils   **sudo aa-genprof firefox**    sudo aa-enforce firefox ...
Why did you run **sudo aa-genprof firefox**?

---

### Post by jamal5 on 2014-11-08
> **vasa1 said:**
> Why did you run **sudo aa-genprof firefox**?

aa-genprof generates a profile for the selected program right? What's the issue here?

---

### Post by vasa1 on 2014-11-08
> **jamal5 said:**
> aa-genprof generates a profile for the selected program right? What's the issue here?Why didn't you use the profile supplied by default?

---

### Post by jamal5 on 2014-11-08
> **vasa1 said:**
> Why didn't you use the profile supplied by default?

I thought firefox isn't apparmor'd by default? Sorry, I'm a bit of a noob to this, I just read the apparmor sticky and went off that... Could you tell me how to do that?

---

### Post by vasa1 on 2014-11-08
> **jamal5 said:**
> I thought firefox isn't apparmor'd by default? Sorry, I'm a bit of a noob to this, I just read the apparmor sticky and went off that... Could you tell me how to do that?You are right in that the profile for Firefox isn't enforced by default. But it can be turned on. 

See [http://askubuntu.com/questions/76412/why-do-i-have-to-enable-the-apparmor-profile-for-firefox-why-isnt-it-on-by-d](http://askubuntu.com/questions/76412/why-do-i-have-to-enable-the-apparmor-profile-for-firefox-why-isnt-it-on-by-d).

Now I'm not sure whether what you have already done has caused the default profile to be overwritten or not.

The profiles should be in /etc/apparmor.d, IIRC. Could you put up the output of **ls /etc/apparmor.d**?

Even if you've damaged the default Firefox profile, you could get it again but I'll have to search for the link. It's been a while since I played with Apparmor! It appears that **sudo apt-get --reinstall install firefox** is all that you need to do to get back the original profile (assuming you've deleted anything related to Firefox in /etc/apparmor.d). See the answer by Lekensteyn here: [http://askubuntu.com/questions/49940/how-to-get-back-the-firefox-apparmor-profile-after-deleting-it](http://askubuntu.com/questions/49940/how-to-get-back-the-firefox-apparmor-profile-after-deleting-it)

---

### Post by jamal5 on 2014-11-08
> **vasa1 said:**
> You are right in that the profile for Firefox isn't enforced by default. But it can be turned on. 

See [http://askubuntu.com/questions/76412/why-do-i-have-to-enable-the-apparmor-profile-for-firefox-why-isnt-it-on-by-d](http://askubuntu.com/questions/76412/why-do-i-have-to-enable-the-apparmor-profile-for-firefox-why-isnt-it-on-by-d).

Now I'm not sure whether what you have already done has caused the default profile to be overwritten or not.

The profiles should be in /etc/apparmor.d, IIRC. Could you put up the output of **ls /etc/apparmor.d**?

Even if you've damaged the default Firefox profile, you could get it again but I'll have to search for the link. It's been a while since I played with Apparmor! It appears that **sudo apt-get --reinstall install firefox** is all that you need to do to get back the original profile (assuming you've deleted anything related to Firefox in /etc/apparmor.d). See the answer by Lekensteyn here: [http://askubuntu.com/questions/49940/how-to-get-back-the-firefox-apparmor-profile-after-deleting-it](http://askubuntu.com/questions/49940/how-to-get-back-the-firefox-apparmor-profile-after-deleting-it)

OK, so I reinstalled firefox, then ran **ls /etc/apparmor.d** here 

[ATTACH=CONFIG]257821[/ATTACH]

It's Xubuntu as you can see not Ubuntu but I don't think that matters here. Still set on complain under aa-status...

Under the reinstall what it did was:

sudo apt-get --reinstall install firefox 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 0 B/35,8 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 174557 files and directories currently installed.)
Preparing to unpack .../firefox_33.0+build2-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox (33.0+build2-0ubuntu0.14.04.1) over (33.0+build2-0ubuntu0.14.04.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up firefox (33.0+build2-0ubuntu0.14.04.1) ...
Please restart all running instances of firefox, or you will experience problems.


It didn't give me any of the options it showed on the askubuntu page by Lekensteyn...

Thanks a lot for helping out

---

### Post by jamal5 on 2014-11-08
Forgot to mention, before I did all that I ran

sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
[sudo] password for user: 
Setting /etc/apparmor.d/usr.bin.firefox to enforce mode.

So that profile says it's in enforce mode but aa-status doesn't agree....

---

### Post by vasa1 on 2014-11-08
In this forum we prefer that terminal information is copy-pasted within ```

``` tags rather than provided as screenshots: it just makes it easier to read and to quote in subsequent posts.

All the same, I'm out of my depth here because I haven't messed with Apparmor for quite sometime. Plus you seem to be using virtualization. All beyond me!

And this part of your image is something I've never seen before in apparmor-related posts: subset of original image attached

---

### Post by maglin2 on 2014-11-08
I believe that all you have to do to set the default apparmor firefox profile to enforce is to remove the shortcut to usr.bin.firefox from /etc/apparmor.d/disable. Then reboot.

(edit - and save it somewhere handy in case you want to put it back)

---

