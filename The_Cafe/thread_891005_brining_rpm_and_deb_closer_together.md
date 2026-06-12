---
title: "brining rpm and deb closer together?"
date: 2008-08-15
forum: The Cafe
---

### Post by bone2006 on 2008-08-15
I know I should use the repositories first, then deb files built for ubuntu, but I know we've all come across one time or another that there's only a rpm file out there..............so we're forced to use alien or not use the software at all.

I'm kind of wondering, why isn't there an auto alien?  I mean wine on my system is pretty cool that if I double click an exe it's all taken care of if wine supports it and I really like it with ubuntu.  But it would be nice to have something that if I double clicked on a rpm file that it's converted and then ran in the background.   Seems like it really wouldn't be a hard program, because it would just call apon alien and then debian package manager to run the created file.   

Or has it not been done yet?

---

### Post by SunnyRabbiera on 2008-08-15
Well its possible to run both RPM and .deb on a system but at great personal risk.
But yes it would be nice if there was a tool to automatically convert .rpm to .deb and have it work without using the terminal.

---

### Post by picpak on 2008-08-15
Clicking an .rpm should:
1) Check to see if it's already in the repositories and
2) if not, auto-convert it with alien and install it.

Who's with me?

---

### Post by SunnyRabbiera on 2008-08-15
> **picpak said:**
> Clicking an .rpm should:
1) Check to see if it's already in the repositories and
2) if not, auto-convert it with alien and install it.

Who's with me?

yeh a small script like that will be useful, but is it plausible?
Alien would be needed and it would need sudo access.

---

### Post by xebian on 2008-08-15
> **bone2006 said:**
> I know I should use the repositories first, then deb files built for ubuntu, but I know we've all come across one time or another that there's only a rpm file out there..............so we're forced to use alien or not use the software at all.

I'm kind of wondering, why isn't there an auto alien?  I mean wine on my system is pretty cool that if I double click an exe it's all taken care of if wine supports it and I really like it with ubuntu.  But it would be nice to have something that if I double clicked on a rpm file that it's converted and then ran in the background.   Seems like it really wouldn't be a hard program, because it would just call apon alien and then debian package manager to run the created file.   

Or has it not been done yet?

It's easy as 123.  Just add alien to your application helpers, and then set the filter to *.rpm to run alien.:guitar:

---

### Post by picpak on 2008-08-15
> **SunnyRabbiera said:**
> yeh a small script like that will be useful, but is it plausible?
Alien would be needed and it would need sudo access.

Heck, you could do it with just bash and zenity; just have a progressbar show alien's progress, then prompt gdebi to install the created deb.

It's searching the repositories that'd be the hard part, because rpm and deb-based systems sometimes have different names and folders for different programs.

---

### Post by xebian on 2008-08-15
> **picpak said:**
> Heck, you could do it with just bash and zenity; just have a progressbar show alien's progress, then prompt gdebi to install the created deb.

It's searching the repositories that'd be the hard part, because rpm and deb-based systems sometimes have different names and folders for different programs.

alien -i  option will install automatically.

---

### Post by picpak on 2008-08-15
> **xebian said:**
> alien -i  option will install automatically.

Now that's slick!

Now for the repo-search part: any takers?

---

### Post by xebian on 2008-08-15
> **picpak said:**
> Clicking an .rpm should:
1) Check to see if it's already in the repositories and
2) if not, auto-convert it with alien and install it.

Who's with me?

What's the point of getting an rpm files in the first place?  Because it's not in the repos, or you want a better version.

---

### Post by picpak on 2008-08-15
> **xebian said:**
> What's the point of getting an rpm files in the first place?  Because it's not in the repos, or you want a better version.

Maybe I should clarify myself: something that checks for conflicts with existing programs, or something to that effect. You know how dependency hell goes.

Or maybe I'm not making any sense at all...

---

### Post by xebian on 2008-08-15
> **picpak said:**
> Maybe I should clarify myself: something that checks for conflicts with existing programs, or something to that effect. You know how dependency hell goes.

Or maybe I'm not making any sense at all...

Yes and no.  alien takes care of the conversion from rpm -> deb format. Once it's in deb format, APT takes care of the rest - including dependency checking, just like any other deb file.

---

### Post by Oldsoldier2003 on 2008-08-15
my thoughts on the whole alien thing...

If you cant find the deb in the repos, compile it form source. Alien is a last resort kind of thing, and shouldn't be made a no brainer point and click. Of course that is just my personal feeling on the matter.

---

### Post by picpak on 2008-08-15
> **Oldsoldier2003 said:**
> my thoughts on the whole alien thing...

If you cant find the deb in the repos, compile it form source. Alien is a last resort kind of thing, and shouldn't be made a no brainer point and click. Of course that is just my personal feeling on the matter.

Depends what it is. Something small like Nitrogen or sakura wouldn't hurt from an alien conversion, but something huge and essential like a kernel probably would.

---

### Post by Superkoop on 2008-08-15
> **Oldsoldier2003 said:**
> 
If you cant find the deb in the repos, compile it form source.

That's what I believe also, if a program isn't in the repos; just compile it. And for easy updating, just use SVN and then don't run make install, and just link to the binary. And then when you want to update, just run an svn update, and recompile. (And to make it even easier, make a script for it)

Assuming you want the latest stuff, and don't mind a bit of breakage. But considering you are willing to use .rpm, I don't think breakage is as big of a deal to you.

---

### Post by bone2006 on 2008-08-17
Well I think it's like the deb files, they do check the repositories first don't they? 
It really doesn't seem like it would be difficult for ubuntu to add the capability that it would convert, check repository, warn and then allow you to continue.

I think options and how easy things are is generally better. I think having an auto system would not hurt anything.  You'd still have the old way of doings things, it's not going to stop you from compiling the software.  If you prefer to convert the file yourself you can still do it with the terminal, so I just see it helping, not hurting.

I an can see why people would say alien is a last resort, which who is to say it's still not a last resort if it was automated?  I try to get 99.99% of my software from the repositories and everything else is last resort.

When I hear people from bsd and apple say things about Linux, believe it or not it's about the deb, compiling, rpm issue and how Linux can't come together for a standard.   It's just like to move forward and the deb versus rpm isn't going to end, but having something that's automated I would really like even if I don't use it at all.

Would you tell your grandmother who got linux working recently to compile an application or you'll be right over to help.  The easier things become I think more users will move over to Linux.

---

### Post by 2cute4u on 2008-08-18
> **Oldsoldier2003 said:**
> my thoughts on the whole alien thing...

If you cant find the deb in the repos, compile it form source. Alien is a last resort kind of thing, and shouldn't be made a no brainer point and click. Of course that is just my personal feeling on the matter.

I find that do be an incredibly elitist attitude.  The point of Ubuntu is to accessable to the average person, most of whch don't even know what compiling from source means, let alone know how to do it.   There are lots of programs that are only available as rpms and not deb, and they should be an easu way to uinstall them.  So to say there shouldn't be a no brainer solution, is to say that those of us who need a no brainer solution, shouldn't have the freedom to use them.

---

### Post by Lord C on 2008-08-18
> **picpak said:**
> Clicking an .rpm should:
1) Check to see if it's already in the repositories and
2) if not, auto-convert it with alien and install it.

Who's with me?

+1 for Interpid?

---

### Post by bone2006 on 2008-08-18
Wouldn't everybody be happy if there was a warning telling the user that they should get it from the repository first, then get the source/deb and last resort to run this to install?

I believe a lot of people agree that getting the software from the repository is of course the best, so I think a warning I can't see why it wouldn't make everybody happy.

---

### Post by kirsis on 2008-08-18
> **2cute4u said:**
> I find that do be an incredibly elitist attitude.  

+1: if alien works, the average user will use it instead of compiling anything (more time consuming). If it doesn't, feel free to compile away.

I don't see how compiling on your own beats alien on the user-friendly scale :)

Here you go, everybody who's interested:

> 
#!/bin/bash

cd /tmp

# Pre-authenticate, so zenity doesn't show up too soon
AUTH=`gksudo --description "Alien binary package installer" -- echo "valid"`

if [ "$AUTH" = "valid" ]; then
	# If authentication was successful, gksudo won't prompt again. Now run alien and 'grep' out the generated filename (alien changes i586 to i386, for example)
	DEB_NAME=`gksudo -- alien --to-deb $1 -v | tee >(zenity --title "Alien" --progress --pulsate --auto-close --auto-kill --text="Converting the package ...") | grep generated`
	DEB_NAME=${DEB_NAME%\ generated}

	# Chown the generated file so we can clean up after ourselves
	USERNAME=`whoami`
	gksudo -- chown $USERNAME "/tmp/$DEB_NAME"
	gdebi-gtk "/tmp/$DEB_NAME"

	rm "/tmp/$DEB_NAME"
else
	zenity --error --text "Invalid password!"
fi


Put this script in /usr/bin (I created /usr/bin/alien2. Don't forget to chmod +x it), then right click an rpm package and open it with a custom command (enter your filename: alien2 in my case) and voila. Launch from nautilus.

It expects absolute filenames, so if you run it from CLI, don't give it relative filenames.


I tested it out with a skype rpm, it seemed to work ok (I didn't proceed with the actual isntall). It creates a deb package in /tmp that gets deleted when you're done with it.

---

### Post by bone2006 on 2008-08-22
Thanks kirsis

I'll give it a try

---

