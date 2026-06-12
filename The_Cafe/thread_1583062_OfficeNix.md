---
title: "OfficeNix"
date: 2010-09-27
forum: The Cafe
---

### Post by GCoffee on 2010-09-27
Hi Guys,

------------------------------------------------------------------
First Off: I couldn't find a relevant forum for this, so apologies
if it's in the wrong forum, feel free to move it.
------------------------------------------------------------------

Anyway, I've been having a bit of a think. I haven't been able to find a Linux distro built entirely for offices, or places of work. Presumably, if an employer wanted to save on their tech bill, Linux would be ideal, but there isn't a distro around that has software suitable for office preinstalled.

I was thinking we could get together, and some volunteers can help make a Office Distro based on Ubuntu 10.04 LTS. Using a LTS edition of ubuntu makes more sense than using the upcoming 10.10 release, as the support for 10.10 will (relatively) quickly fade, and upon release may be unstable, but 10.04 has been around for a while now, so now major bugs will appear.

Anyway, at the moment the idea is in the brainstorming stages, Currently i've installed VirtualBox, and downloaded a 10.04 standard x32 ISO which i'm going to install to VirtualBox.

Some obvious choices for software which i've quickly thought up:

 - Open Office
 - Adobe PDF Reader
 - Mozilla Firefox (Maybe preinstalled plugins such as NoScript?)
 - Remove GNOME Games.

Any other suggestions for software that is already available and open source, as well as suggestions for software that could be made would be welcome.

Some prospective features i've thought about:

 - Ability to monitor employee's work (VNC?)
 - Quick and easy config tool on first setup to choose what        packages they would install (Office,VNC,Firefox)
 - Again, some sort of easy tool for admins to setup network shares.
 - Block access to terminal for standard users (security issues, etc)

Again, other suggestions for features are welcome.

I've chosen ubuntu mainly because of it's strong community, as well as it's out-of-the-box easy usability in general.

Any questions, suggestions, constructive criticisms, do post.

Thanks,
GC.

**EDIT:** Sorry for the double post, must've hit the submit button twice.

---

### Post by robsoles on 2010-09-28
Right forum area for this is the community cafe - don't stress, a mod will notice soon enough and shift it quite nicely. (If not we can always bring it to their attention via the resolution centre).

I am the IT of the small company I work for and we are using Ubuntu on the best computers here.

10.04 LTS installs out of the box ready with OpenOffice, Evince (PDF reader), Evolution (email, much as I prefer thunderbird) and a raft of useful programs for home or office.

User's can be left with terminal access, what can they do if they can't sudo?

Using VNC to view your employee's screen is probably fair enough but really their output should be measurable and if they produce more than the others and you catch them playing solitaire all the time it would probably be dumb to gripe at them for playing, they are producing more than the others...

Networking in 10.04 LTS is a breeze, samba is managing DC role quite well for the local domain and there are no issues between windows and Ubuntu users on this network.


Not saying it's not worth pursuing your idea but am saying the hard yards are mostly covered for you already!

---

### Post by mastablasta on 2010-09-28
> **GCoffee said:**
> 
Anyway, I've been having a bit of a think. I haven't been able to find a Linux distro built entirely for offices, or places of work. Presumably, if an employer wanted to save on their tech bill, Linux would be ideal, but there isn't a distro around that has software suitable for office preinstalled.

 
Seriously? i think this is what Canonical does. Check their website. Also Red Hat.
 
They will build you a distro specifically suited to your business needs.
 
 
 
----
 
On a side note i only miss internet banking with Ubuntu, but it't not up to Ubuntu or Linux ocmmunity to resolve that as my bank needs IE to run it.

---

### Post by cariboo on 2010-09-28
This isn't a support question, moved to the Cafe.

---

### Post by beew on 2010-09-29
>  Ability to monitor employee's work (VNC?)

This is a prime example of how technology is deployed for anti human ends and why there is an anti-tech ethos in many parts of society. 

How about installing monitors for bathroom breaks? Sick.

---

### Post by NightwishFan on 2010-09-29
I agree that Ubuntu does have those ends covered. I think this could be well covered with an optional add-on metapackage. It installs and changes defaults to:

[LIST]
[*]Easily visible theme that reduces eyestrain.
[*]Inkscape and other great office apps.
[*]Large amount of extra high quality fonts and templates.
[*]Wine and a guide to install supported office apps?
[/LIST]

---

### Post by MrNatewood on 2010-09-29
Isn't this covered by OpenSUSE\SLED?

---

### Post by grahammechanical on 2010-09-29
I had a look at Ubuntu Studio yesterday. It has a fantastic look to it. Really impressive. Those guys are taking the same approach as has been suggested here. Tailor a distro for a certain set of users. There might be a place for such a distro. It might impress the bosses.

I would leave out synaptic and the software centre except for installation on an administrator's computer/desktop. I would include crafted PDF installation and help files specifically for this distro and its uses.

regards.

---

### Post by GCoffee on 2010-09-29
I was indeed thinking along grahammechanical's line of thinking. I'd agree, specific help files and PDF support built in would be a good idea..

Also, maybe have Java preinstalled?

 - Ben.

---

