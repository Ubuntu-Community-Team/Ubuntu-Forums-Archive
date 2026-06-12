---
title: "Samba SWAT - Creating New Share Overwrites Previous ones in smb.conf"
date: 2008-07-22
forum: Server Platforms
---

### Post by AoiShikaku on 2008-07-22
Hi,

I have a problem with Samba SWAT.  I've tried almost everything I could possibly think of trying to get this to work, but it just a reoccurring problem no matter what I do.

[COLOR="Red"]**[PROBLEM]**[/COLOR]
When I go to create a new share using Samba SWAT it over writes the previous share so I can't create multiple shares using SWAT.  I can only have one before it deletes the previous ones.

[COLOR="Red"]**[THINGS I DID, BUT PROBLEM STILL EXISTS]**[/COLOR]
- Uninstall and Reinstall Samba
- Uninstall and Reinstall Samba-SWAT
- Uninstall and Reinstall Linux + SAMBA + SWAT


Now I know I can manually input all the shares through the smb.conf file, but I have over a hundred shares that I need to create, which is simply an annoyance, and will be a pain in the butt when I have to add more for the future.

I'd just like things a little simplified through the web interface than having to use two things to do the job that one is _supposed_ to do.

---

### Post by cariboo on 2008-07-23
Your going at this from a windows viewpoint. Just because something doesn't work the way you expect it to, you shouldn't have to go through the routine of uninstalling then reinstalling.

How are you going about adding shares, are you clicking on the shares button to add shares, or are you using the wizard button, cause I just tried it and it doesn't seem to work.

Jim

---

### Post by windependence on 2008-07-23
cariboo, you took the words right out of my mouth. :)

Since when does installing and reinstalling ever fix a problem? Maybe on 'doze, but certainly not on 'nix.

OK that being said, now to the problem.

Adding shares to the conf file is trivial at best and if vi scares you, use an editor like nano or pico.

A better idea would be to write yourself a small simple script (like a batch file in Windoze) to automate the task of adding shares and users at the same time. I am just guessing you are trying to do that. If you google what you are trying to do, there is probably already a script out there that someone has written for this. If it's inconvenient for you, it's probably inconvenient for someone else.

Why are you adding so many shares? Are you trying to add a share for each user?

One last thing, you may consider installing Webmin if you MUST have a web interface because it includes SWAT and much more.

-Tim

---

### Post by AoiShikaku on 2008-07-23
> **cariboo907 said:**
> Your going at this from a windows viewpoint. Just because something doesn't work the way you expect it to, you shouldn't have to go through the routine of uninstalling then reinstalling.

How are you going about adding shares, are you clicking on the shares button to add shares, or are you using the wizard button, cause I just tried it and it doesn't seem to work.

Jim

Well there were a lot of complications aside from this problem, and it was a lot faster to reinstall everything than to troubleshoot.  Why spend 5 hours on something where you can get it up and running again in 1 hour.

I have it perfectly setup on a RedHat box but that was configured a while ago and I haven't upgraded it to the newest version because if it isn't broken and it does the job I tend to leave it going.

Anyhow, back to the SWAT issue I am having, there are several tabs available on there.  Generally all you have to do is click on the shares tab, type whatever you want in the "create share" area and click "click share" and it should add that share to the drop down menu and also write to the smb.conf, but that's not happening.  I've also checked out the wizard from the SWAT page and there is no way to create a new share through there.


> **windependence said:**
> cariboo, you took the words right out of my mouth. :)

Since when does installing and reinstalling ever fix a problem? Maybe on 'doze, but certainly not on 'nix.

OK that being said, now to the problem.

Adding shares to the conf file is trivial at best and if vi scares you, use an editor like nano or pico.

A better idea would be to write yourself a small simple script (like a batch file in Windoze) to automate the task of adding shares and users at the same time. I am just guessing you are trying to do that. If you google what you are trying to do, there is probably already a script out there that someone has written for this. If it's inconvenient for you, it's probably inconvenient for someone else.

Why are you adding so many shares? Are you trying to add a share for each user?

One last thing, you may consider installing Webmin if you MUST have a web interface because it includes SWAT and much more.

-Tim

I thought about the script idea, but theoretically SWAT should do exactly that for me and it would be easier just to have one thing do everything I need to use it for than having multiple things just to configure one thing.

The reason for all the shares is because there are A LOT of users, groups, and different locations for everything.  I do have webmin setup for the BIND DNS, but it lacks the control for a Domain Controller so it isn't as useful to me.



In theory, this is the newest available version of samba-swat installed and, keep this in mind, everything straight until the point of having my shares being overwritten when I try to create a new one only exists in this version because I have it up and running on my RedHat box.  If you think it's a bug then call it, but if you think I did something wrong and can point me in the right direction that would greatly be appreciated.

---

### Post by windependence on 2008-07-23
Couldn't find anything when I googled it so it's probably something in your config.

Does SWAT have a batch mode where you can add bulk users? I'm just curious why it wouldn't be faster to edit the config file. I haven't used SWAT or Webmin in years. All CLI now for me since I became a FreeBSD borg. :)

-Tim

---

### Post by AoiShikaku on 2008-07-23
> **windependence said:**
> Couldn't find anything when I googled it so it's probably something in your config.

Does SWAT have a batch mode where you can add bulk users? I'm just curious why it wouldn't be faster to edit the config file. I haven't used SWAT or Webmin in years. All CLI now for me since I became a FreeBSD borg. :)

-Tim

Yeah I checked google and the Samba forums with no luck so I thought I'd ask here.  I went over the config file so many times now I can't seem to pin point exactly what it is nor do I see any error.  I am starting to believe it's a bug in SWAT.  I'm in the middle of a RedHat ES3 install on another server to see if it is a bug or not in the newest SWAT available.  If it's giving me this much trouble it's not worth messing around with when there are other stable versions out there.

I just like SWAT because everything is listed for you.  I want to use this server as a Domain Controller editor.  As far as  the users and groups go, I'm just going to search for something to convert the NT users and groups over to the Linux box.  I know I could simplify things even more by buying a 2003 license but it's the money factor that my company isn't willing to spend on.

---

### Post by cariboo on 2008-07-23
One more question might be stupid but here goes, are you running swat as root? Thats the reason I don't use swat anymore.

Jim

---

### Post by AoiShikaku on 2008-07-24
> **cariboo907 said:**
> One more question might be stupid but here goes, are you running swat as root? Thats the reason I don't use swat anymore.

Jim

Yeah I am, you can either setup users or just use your local account name and pass, but that one limits your access to stuff.  More like a read only to only a certain number of things on SWAT

---

### Post by HermanAB on 2008-07-24
Hmm, I'd recommend that you don't use Swat.  Rather use Webmin, since Swat is generally just baaaaaaadddd.

Cheers,

Herman

---

### Post by AoiShikaku on 2008-07-24
> **HermanAB said:**
> Hmm, I'd recommend that you don't use Swat.  Rather use Webmin, since Swat is generally just baaaaaaadddd.

Cheers,

Herman

I'm actually using both, but I need SWAT to make the shares.  I'd like it if Webmin had good domain controller settings, but saddly I've gotta resort to SWAT.  It would simplify things though if they did.




Anyhow, I've given up trying to get it up and running and put up RedHat Enterprise Lunix 4 and had it work with no problems at all.  SWAT and Webmin are fully functional now.

I'm thinking it was a bug in the coding between the HTML and before the smb.conf.  That's now SWAT's problem to fix that now.

but thanks none the less for the attempts.

---

### Post by HermanAB on 2008-07-24
You need the Virtualmin plugin for Webmin to manage domains.

Cheers,

Herman

---

### Post by herzbube on 2008-09-14
I had the same problem on Debian using the swat package version 2:3.2.0-4. I did not find the source of the problem, but it silently went away after I upgraded to package version 2:3.23-1. I guess it was a bug in swat after all...

Reference to Debian bugtracker: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=496597](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=496597)

Cheers
Patrick

---

