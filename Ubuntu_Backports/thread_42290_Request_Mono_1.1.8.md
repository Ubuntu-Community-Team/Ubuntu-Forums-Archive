---
title: "Request Mono 1.1.8"
date: 2005-06-16
forum: Ubuntu Backports
---

### Post by Ozitraveller on 2005-06-16
I've just noticed that Mono 1.1.8 has been released. This is probably already on the list to do, but I thought I would add it here anyway.

---

### Post by jdong on 2005-06-16
Unless Breezy goes for it, I really don't want to redo mono.

---

### Post by Slo Mo Snail on 2005-06-17
I assume it will take at most a week until it's in breezy ;) We have to rebuild monodevelop after backporting mono 1.1.8 as it includes the new debugger and a monodevelop with debugger support would be nice ;)

---

### Post by Redth on 2005-07-15
I'd love to see 1.1.8 as well, just wondering what the status is on it :)

---

### Post by sebgate20 on 2005-07-15
There is a way to get Mono 1.1.8 working sucessfully on Hoary using the Debian packages. I am writing a HOWTO now and will post a link later.

Seb

---

### Post by Redth on 2005-07-15
wonderful!

---

### Post by manicka on 2005-07-15
1.1.7 works just fine for me and is very stable. I'm happy to leave it until 1.1.8 is in backports in a few weeks.

---

### Post by Redth on 2005-07-15
well, I'm somewhat interested in the System.Windows.Forms implementation (which I can't even get working properly with 1.1.7 packages on the backports), so there will be some significant changes between 1.1.7 and 1.1.8 in that area.

---

### Post by reformist on 2005-07-17
Improved windows forms is a big deal for a lot of people. I'm interested in having it so people can try [this craziness](http://primates.ximian.com/~lluis/blog/pivot/entry.php?id=40)  in MonoDevelop, which requires NUnit (which is now shipping again in Mono 1.1.8). However, that stuff is only in MonoDevelop svn, so, to try it one would already have to be building from source... Might not be worth consideration until breezy.

---

### Post by Redth on 2005-07-17
Hopefully sebgate20 will post a guide soon.  I'm really itching to get at this, but really don't want to go and install 1.1.8 from source :/ I agree, Windows.Forms is a big deal for many.  Now wouldn't it be nice to see a windows.forms designer in MonoDevelop?

---

### Post by Alexandre on 2005-07-26
[QUOTE=jdong]Unless Breezy goes for it, I really don't want to redo mono.[/QUOTE]

Mono 1.1.8 is being used by Breezy and libgdiplus 1.1.7 also. Both are needed in order to get WindowsForms support.

Is there any chance of getting this version on backports?

What could I do in order to help in the process?

---

### Post by davidsf on 2005-07-26
[QUOTE=Alexandre]Mono 1.1.8 is being used by Breezy and libgdiplus 1.1.7 also. Both are needed in order to get WindowsForms support.

Is there any chance of getting this version on backports?

What could I do in order to help in the process?[/QUOTE]

I have backported libgdiplus 1.1.7 and mono 1.1.8.2 (and lastest beagle and tomboy)

You can grab it from : [http://www.gnome.org/~davidsf/ubuntu/hoary/mono/](http://www.gnome.org/~davidsf/ubuntu/hoary/mono/)

cheers

---

### Post by charlieg on 2005-07-26
[QUOTE=davidsf]I have backported libgdiplus 1.1.7 and mono 1.1.8.2 (and lastest beagle and tomboy)

You can grab it from : [http://www.gnome.org/~davidsf/ubuntu/hoary/mono/](http://www.gnome.org/~davidsf/ubuntu/hoary/mono/)

cheers[/QUOTE]
 Please oh please can somebody pull these into the official backports!? :)

---

### Post by manicka on 2005-07-27
[QUOTE=charlieg]Please oh please can somebody pull these into the official backports!? :)[/QUOTE]
 I'd be curious as to how many people can get them to work properly. I've installed all packages without any dep problems but they completely break the versions of Beagle and Tomboy available here as well. I cannot start beagled, best or Tomboy.

---

### Post by davidsf on 2005-07-27
[QUOTE=manicka]I'd be curious as to how many people can get them to work properly. I've installed all packages without any dep problems but they completely break the versions of Beagle and Tomboy available here as well. I cannot start beagled, best or Tomboy.[/QUOTE]

It's strange, because I can run all these apps just fine.

What error do you have when running the apps in console ?

---

### Post by manicka on 2005-07-27
[QUOTE=davidsf]It's strange, because I can run all these apps just fine.

What error do you have when running the apps in console ?[/QUOTE]
 In Tomboy I get no messages in the console, it just hangs and the I get a popup that says the program has quit unexpectedly. I never ran it in debug mode so don't have any more info.

By beagle log shows just showed the floowing after the program failed to load.

05-07-27 17.47.23.17 08922 Beagle DEBUG: Command Line: /usr/lib/beagle/BeagleDaemon.exe  --bg
05-07-27 17.47.23.47 08922 Beagle DEBUG: Starting main loop
05-07-27 17.47.23.48 08922 Beagle DEBUG: Starting messaging server

I've had a go at this twice now and am a bit gun shy of spending the time on fixing it up again if i can't get it to work. It takes a while to move back to mono 1.1.7, beagle etc and resolve all the dependencies from the 1.1.8 uninstall.

---

