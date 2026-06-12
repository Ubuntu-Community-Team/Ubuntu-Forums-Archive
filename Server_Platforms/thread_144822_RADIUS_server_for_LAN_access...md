---
title: "RADIUS server for LAN access.."
date: 2006-03-15
forum: Server Platforms
---

### Post by bushtor on 2006-03-15
Hi,

I plan use an ubuntu server with samba 3 as domain controller plus file- and print services for around 300 users.

In addition to the above mentioned classroom network, we need to have users authenticate themselves before getting access to the internet in the school's dorm areas.  

I have been told that a neat solution for this would be to run firewall with a radius server using LDAP to communicate with the domain controller so the students use the same login usernames/passwords in the dorm areas as they do in the classrooms.

The goal is that there should be no possibility to gain any access to the internet (from the wired LAN) without having logged in to the radius server.

Any comments or suggestions on this approach?

I have tried to browse the forums for radius server stuff, but most of it is related to wireless networking.  Does it exist a good radius server with ubuntu howto somewhere? 

I'm also interesting in installing webmin for the ubuntu server.  However there are piles of posts with warnings and comments on webmin installs with ubuntu.  Does it exist an 'official' howto for webmin?

best regards

Tor

---

### Post by sjpwong on 2006-03-25
I'm working through a lot of similar issues setting up an Internet cafe at the moment.

The application I am using is chillispot.  The home page is [www.chillispot.org](www.chillispot.org) and there's an Ubuntu wiki page too! There's a debian package at their site which works fine for Breezy.

It works really well for what you want - it's called a captive portal.

The radius server I am using is freeradius ([www.freeradius.org](www.freeradius.org)) that can be configured to use MySQL as the backend or a million others like LDAP.

I haven't used webmin.

Hope this helps...good luck!

---

### Post by ev5unleash1 on 2007-09-25
Ok, Well I'm trying the same thing to get a RADIUS server on my Ubuntu server. Don't ask me why I'm just practicing how protective I can be on a network and how protective I can get a network. I have tried FreeRADIUS but linux programs that arent designing for a pasific distro like Ubuntu is annoying and I never installed a program like that in my life and I don't plan on it. Is there any .deb RADIUS server packages out there.

---

### Post by HermanAB on 2007-09-26
Hmm, unless you have millions of users on your LAN, RADIUS is overkill.  I'd suggest that you just use Samba as a domain controller.

---

### Post by wirelessmonkey on 2007-09-26
Um... freeRADIUS is available via the repos, hence a .deb

---

### Post by ev5unleash1 on 2007-10-07
I know but I don't know how to use it.

---

### Post by HermanAB on 2007-10-07
Here you go:
[http://www.aeronetworks.ca/radius.html](http://www.aeronetworks.ca/radius.html)

Cheers,

H.

---

### Post by Doc.Caliban on 2007-10-17
> **wirelessmonkey said:**
> Um... freeRADIUS is available via the repos, hence a .deb

The currently available RADIUS version from the repository is 1.1.3.  I would like to install the latest stable version, 1.1.7, but the prebuilt deb's I have found so far have not worked well.  Is there an "official" ubuntu repos I can get this from?

Thank you,

-Doc 

(On the verge of installing plain old Etch)

---

### Post by ev5unleash1 on 2007-11-02
I have Samba on my server. How do i use that to authenicate users on my network?

---

### Post by HermanAB on 2007-11-02
See the Official Samba Howto on the samba web site.  It is a really good guide.

Cheers,

H.

---

