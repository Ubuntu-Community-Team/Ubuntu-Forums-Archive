---
title: "Linux Desktop Management Tools like Active Directory?"
date: 2009-12-04
forum: The Cafe
---

### Post by dmengo on 2009-12-04
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]I&#8217;ve recently been taking a look at Ubuntu, Linux Mint, and Fedora on the desktop to see how the Linux operating system works. I consider myself a beginner with Linux, but I'm interested in learning more.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]I'll share a bit of background about myself. I have ten years of experience supporting and administering almost exclusively Windows desktops. Along the way I acquired the typical skill set for managing Windows desktops including experience with Windows Server products, Active Directory, Group Policy, VBScript/PowerShell scripting, ImageX for imaging and deployments, etc. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]I&#8217;d like to broaden my skills by studying and learning how to support and manage Linux desktops to be more &#8220;well-rounded&#8221; in my field. I&#8217;m also considering studying and eventually going for the LPI and Linux+ certifications.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]I&#8217;m curious, other than Novell products are there similar tools like Active Directory and Group Policy for managing large numbers of Linux desktops in the enterprise? What about imaging, operating system upgrades, and software deployment products for Linux?[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by phrostbyte on 2009-12-04
This is good for system management:
[http://www.canonical.com/projects/landscape](http://www.canonical.com/projects/landscape)

There is also a installer file format that lets you automate installs. I forgot what it's called.

---

### Post by dmengo on 2009-12-04
I'll take a look at that product from Canonical.  Desktop management tools will help to make Linux on the desktop more of a reality in my opinion.

I probably should have posted this topic in the development forums.

---

### Post by FuturePilot on 2009-12-04
Active Directory ----> LDAP

---

### Post by dmengo on 2009-12-04
> **FuturePilot said:**
> Active Directory ----> LDAP

Yes, Active Directory uses LDAP for its directory services.  Directory services covers the machine logon, authentication, access to file shares, resources, etc.

The use of Group Policy with Active Directory is an essential tool for managing Windows desktops, servers, users, groups, etc.  Novell also has their own tools and directory services for managing Linux desktops.  I was curious to see if there were others available.

---

