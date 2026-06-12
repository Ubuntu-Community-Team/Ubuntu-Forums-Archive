---
title: "Security Company IT"
date: 2008-02-09
forum: The Cafe
---

### Post by randomnote1 on 2008-02-09
I have just come across and opportunity to design the IT for a startup security company.  The owner is planning on growing this business into a multi-billion dollar business over the next five years, so the growth challenges are going to be immense.  I'm not 100% sure of what the business model will look like, but I do know that there will be security officers out in the field and the owner wants to work out of his home (at least to start). 

The security officers will be armed with laptops, cell phones, and digital cameras.  They will upload their pictures to a central database from which I think it would be nice if the customer could access and view these images.

The owner has a few other employees who he would like to conference live with throughout the course of a normal workday.  I am thinking that something like a VNC connection between these computers would be nice, but I'm not sure if there's anything nicer/better out there that would stimulate better collaboration.

As far as the technical end, I'd really love to have a Unix/Linux backend.  I'm very familiar with Solaris 10 and Ubuntu.  Plus it would be awesome if I can deploy Ubunutu on the client computers.

I'm sure all this is possible with some time and research, but I wanted to see if anybody had some prior experience with starting and growing an IT department of this magnitude.  Thanks in advance!

---

### Post by tcpip4lyfe on 2008-02-09
I am part of a startup company that is growing at an incredible pace.  We started with 4 people and now we're at over 100 and it's only been 1 year and a half.  Let me tell you that it's insane.  Get ready for 60 to 70 hour weeks and say good bye to your family and friends.  But when it takes off, its incredibly rewarding. The first thing you should do is figure out what the employees will need to get their work done.  Obviously they'll need email so I'd take a look at zimbra for your email server.  It's extremely easy to install and is very powerful.  You can set it up as an ldap server and run samba based ldap authentication on it so people could log into the domain and have their picture drives all mapped with batch scripts. Maybe make a web server with a mysql back end that users could upload their pictures into and the customers could view. I'd be extremely hesitant in using anything but XP pro on the desktops. Open office is ok but we've had nothing but problems getting people to save it as the right format, crashing when pulling files over the network, and general slowness.  Plus if the business takes off, it's nice to just pull a workstation out of the box and deploy it instead of reformatting with Ubuntu and wasting a XP license.   You won't have time.  After email,  I'd get a FreePBX server setup with a T1 and get a bunch of IP phones and start with just conference calls and if the need arises, move to video conferencing.   As a start up company, video conferencing doesn't make sense because of cost of bandwidth you'd need. Employees could VPN in and use a softphone to join the conference call if they were in the field.  Maybe add video conferencing when your budget grows. Remember in a start up you have to minimize you IT expenses.  That means things like Netgear routers  and old e machine servers, make your own cables, buy used or refurbished computers for the first couple years until you start making money.  Hope this helps and good luck.

---

### Post by randomnote1 on 2008-02-11
Thanks for the advice.  I checked out Zimbra and it looks really nice.  That is definitely going on the table as a possible solution.

---

