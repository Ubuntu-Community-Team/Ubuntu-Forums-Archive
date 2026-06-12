---
title: "Lotus Notes for Linux, July 24th..."
date: 2006-07-10
forum: The Cafe
---

### Post by acascianelli on 2006-07-10
[http://www.betanews.com/article/IBM_to_Release_Lotus_Notes_for_Linux/1152549356](http://www.betanews.com/article/IBM_to_Release_Lotus_Notes_for_Linux/1152549356)

I will be completely free of Windows and Windows emulate :D

---

### Post by kripkenstein on 2006-07-10
I'm not a fan of Notes, or of software that costs money... but if having Notes on Linux will let some companies decide to switch from Windows, then I guess this is a good development.

---

### Post by acascianelli on 2006-07-10
> **kripkenstein said:**
> I'm not a fan of Notes, or of software that costs money... but if having Notes on Linux will let some companies decide to switch from Windows, then I guess this is a good development.

I know it will become a more appealing option for my company.  Our DB/Mail all run off of Lotus Domino.  I've been kinda the unofficial test mule for testing Lotus Notes under Wine/CXOffice.  CXOffice runs Lotus Notes pretty good but it is still pretty buggy, not to mention it costs money.

---

### Post by rverrips on 2006-07-23
Ok, I've downloaded it, (as per the Passport Adv. site it was available from the 19th??)

Anyway, I am having problems installing it under Ubuntu - The instructions state you need to install the IBM Workplace Managed Client which is included in the download - When I run the install it ends with the error: 

Can not validate Mozilla version

As per the installation docs Mozilla 1.7.12 is needed, which I downloaded from mozilla.org and dropped into /usr/local/mozilla (Is there no longer an Ubuntu package for Mozilla??)

Still getting the error, even though as per the release notes for IBM WCS 2.5 ... 

> When installing the Workplace Rich Client on a Linux workstation, the error "Cannot validate Mozilla version" indicates that version 1.4 of Mozilla with GTK2 binding is not installed on the workstation, or it is not installed in the expected location. 

The file "/etc/gre.conf" contains information on the Mozilla version and the variable "GRE_PATH" whose value should point to the directory location where the appropriate Mozilla version has been installed. In a default RedHat installation this file contains the following information: (*NOTE: The information I tried putting in is beside each line in italics*)
[1.4]  *([1.7] and also [1.7.12])*
GRE_PATH=/usr/lib/mozilla-1.4  *(GRE_PATH=/usr/lib/mozilla-1.2.1)*
To fix this error do the following: 
1. Download Mozilla 1.4 for RedHat from the followin ftp URL "http://ftp.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.4.1/contrib/mozilla-1.4.1-gtk2-xft-svg-calendar-suse82.tar.bz2"  
2. Extract the contents of this file to /usr/lib/mozilla-1.4 directory
3. Create or update "/etc/gre.conf" to have the first two lines as below
[INDENT][1.4] 
GRE_PATH=/usr/lib/mozilla-1.4
[/INDENT]4. Reinstall Workplace Managed Client platform.

I did the above (well, not the RedHat bit) but still no luck, anyone had any success yet?

---

### Post by sigmo on 2006-07-24
I did the following:

# apt-get install mozilla-browser
# cat > /etc/gre.conf
[1.7.12]
GRE_PATH=/usr/lib/mozilla
^D

And after that, installed Lotus Notes without any problem

---

### Post by loupy on 2006-07-24
I was able to get it to install by changing the gre.conf to point to /usr/lib/mozilla-firefox.  But after the install when I run notes all i get is a 2 pane window - the left says "notes applications" and the right says "notes home page."

How do I configure it??](*,)

---

### Post by sigmo on 2006-07-24
I have the same problems. Tried something with X11 forwarding to my work desktop.

I installed the following extra packages: 
- gawk 
- libmotif3

Now notes client does something more, but I'm not sure what's happening now ... Tomorrow I will have a further look. ZZZzzz...

---

### Post by rverrips on 2006-07-25
> **sigmo said:**
> I did the following:

# apt-get install mozilla-browser
# cat > /etc/gre.conf
[1.7.12]
GRE_PATH=/usr/lib/mozilla
^D

And after that, installed Lotus Notes without any problem

Now that makes a whole lot more sense than what I was trying to do *doh*

Installed fine after that, but I also have the empty window with two tabs and nothing much else once it's launched ... I already had gawk and motif loaded to make my Citrix Client work, so that doesn't seem to be the fix?

I'm guessing it also has to do with the fact that my Domino Server is still on version 6.5.5 - The doc's say the minimum Domino version is 7.0.1 (not even 7.0.0) so that may be it?  I have an upgrade scheduled to 7.0.1 next week and guess I'll need to wait 'till then to confirm?

Anyone else had success yet?

---

### Post by rverrips on 2006-07-25
This thread has been continued here: [http://www.ubuntuforums.org/showthread.php?t=222210](http://www.ubuntuforums.org/showthread.php?t=222210)

---

