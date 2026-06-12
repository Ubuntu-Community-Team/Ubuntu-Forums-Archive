---
title: "using edgy eft as a server at work"
date: 2007-04-14
forum: Testimonials &amp; Experiences
---

### Post by jman623 on 2007-04-14
**Note*** I coped and pasted this from a post I replied to in the Community Cafe, I thought it would be more appropriate to paste it here: here's the original thread if anyone is interested: [http://ubuntuforums.org/showthread.php?t=408100]("http://ubuntuforums.org/showthread.php?t=408100")



> I think that a real market for desktop Linux PC are little companies with 5-20 PC-s just starting to grow

I work for one of those types of companies, It's a non profit after school and summer progrram for for at risk youth.


This is a all MS enviroment however this organization cannot afford the licensing that plague Windows Server OSes. So I decided to go the linux route with ubuntu of course:D  So here's what I got cooking:

First of all I actually have ubuntu running in VMware because the people I work for are very technical inept and I don;t want to scare them. ;-)

So I am using Samba 3.0 so the students can have my version of "roaming profiles" I'll get to this in a second ;-)

FTP so i can upload files when I am not at the office, and so I can do image deployment with Ghost4Unix.

Web Server so I can host the company website locally for testing purposes before launching it to our hosting provider.

SSH so i can putty in from any workstation or from home if needed.

UltraVNC running on the Host Windows 2000 pro OS with encryption of course.:mrgreen: 

DynDNS updater since we have basic Verizon Business DSL and they like to change the IP on us everyday.:mad: 

Print Server running on the Host Windows 2k pro OS cause of driver issues.:( 

Still trying to think of a backup scheme.

Ok so here is how I setup the student's roaming profiles; BTW I didn;t do things the "traditional" way because I had a heck of a time getting Samba to work as a PDC.

First off I am using [G4U/]("http://www.feyrer.de/g4u/") for image deployment. So on the PC image I did the following the regedit:

```
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\
User Shell Folders]
```

The students use one account called student ( thats how it was before I stepped in and decided for obvious reasons to keep that way:roll: 

first off on the server I have share called 'Students'. In that folder their are subfolders one for the Desktop, Favorities, Application Data (firefox bookmarks), and Documents which will obviousily be there 'My Documents' folder. In the Documents I have a subfolder  for each student.

I also have Security set to share in smb.conf since I had a hell of time getting samba to work as a PDC, so I decided it really doesn't matter if student's can see each other files.

So in the Regedit I mentioned above ("User Shell Folders") I changed each key that corresponds to the respective folder set up on the server 


For example for the Desktop, I set the Desktop key to:
```

\\<IP of server>\students\Desktop
```

that way no matter what computer they decide to go to they have the same Desktop with the same files and shortcuts. I also disabled the changing of desktop background so we dont have kids argueing over desktop backgrounds plus that can complicate things for me.


I know this isn't the straight forward scenario but it's working for me. I think more effort should be put into Ubuntu Server. It already comes with LAMP and DNS preconfigured why not have Samba and LDAP preconfigured so we can just bascially ditch Microsoft?:confused:

---

