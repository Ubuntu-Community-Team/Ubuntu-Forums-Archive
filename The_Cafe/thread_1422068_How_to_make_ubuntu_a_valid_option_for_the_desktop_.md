---
title: "How to make ubuntu a valid option for the desktop in offices"
date: 2010-03-05
forum: The Cafe
---

### Post by ndefontenay on 2010-03-05
Hi.

I was thinking the following:

As an IT manager in a company (not me, any IT manager) how would I be able to use Ubuntu as the desktop OS while keeping productivity with Microsoft specific tools for example: AutoCAD, Excel with connectivity to Analysis Services and related tools such as SQL Server Management Studio and Visual Studio.

in short, requirements would be as follow:
1)Ubuntu must be installed on all machine
2) All Users should be able to access their usual application. (We suppose a windows migration with a lot of existing systems)
3) Support should be provided remotely by helpdesk.
4) Installation should be easy. An equivalent to Norton ghost should be provided.
5) Users should be managed centrally in the event someone leaves the company, it should be possible to disable an account on a client machine.
6) Backups should be centralized on a server
7) All access should be controlled and on a need to know basis.
8) The whole solution should be easy on the end user (helpdesk or normal user. I don't want the sys admins to create a user on a client machine then the same user name and password on a file sharing server for example, not manually at least)

The immediate benefit is of course lack of license management and therefore cost for the OS and no viruses so no anti viruses solutions = more cost saving

A few investment would be required but I think that with a tool such as Citrix XenApp, it makes the hardest part possible. Training would also be a thick part of the initial investment either in employee spent time or actual provided training.

[http://citrix.utipu.com/app/tip/id/2615/](http://citrix.utipu.com/app/tip/id/2615/)
[http://www.citrix.com/English/ps2/products/product.asp?contentID=186&ntref=prod_top](http://www.citrix.com/English/ps2/products/product.asp?contentID=186&ntref=prod_top)

The user runs the application on a server but sees the application as a new window in his OS. File saving is, I believe local which makes sharing pretty easy.

Do I miss anything to make such a project acceptable to end users and CIO?

Again this is role play, I'm not actually pitching it. I just want to make some content available and prove to CIOs that it's very possible to keep employees happy and productive while benefiting from Ubuntu low cost and security.

The idea of this thread is to build a user case for such requirements.

Third party applications are acceptable if it makes it better. Budget is not a constraint (depends of the size of the organization)

---

### Post by HermanAB on 2010-03-05
Howdy,

Your biggest problem is that you need to configure Active Directory either with Likewise of Samba Winbind.  Then, I would not use ghost/dd but would rather configure Red Hat Kickstart to install the system, since that takes care of hardware differences and changes.  

After the initial heart-ache, going forward with a kickstart install is virtually zero effort even when you completely change all the hardware.

Kickstart is available for Ubuntu somewhere, but it is not the native way to do it.  Anyhoo, if you want a much, much, much easier time with the whole desktop and network install problem, then you should use Red Hat Fedora or Mandriva, not Ubuntu.

---

### Post by madnessjack on 2010-03-05
The biggest problem I can see (making Ubuntu valid for desktop in offices) is the office applications for Windows are very good.

---

### Post by ndefontenay on 2010-03-05
Yes. Active Directory or something similar is, I believe the hardest part of it.

---

### Post by Tibuda on 2010-03-05
If you have to use AutoCAD, MS Office and Visual Studio, you better use Windows.

---

### Post by Techsnap on 2010-03-05
You could look at solutions such as likewise for your active directory. However I recommend that you you use CentOS or Debian over Ubuntu because of the stability factor. CentOS also has a long support schedule which means you won't have to be upgrading the OS on a regular basis.

---

### Post by TBABill on 2010-03-05
+1 on sticking with Windows for software specific requirements in a business. Trying to get a software that natively runs in another OS to work inside another OS may work quite often, but why force and risk that relationship when a business relies on security, stability and consistency? Trying to replicate an expected performance level inside another OS may be difficult and unreasonable for memory intensive and CPU intensive tasks, such as AUTO CAD. 
 
I totally understand the desire to move out of the Windows world, as I have mostly done myself, but if your need resides in Windows I'd think staying there may be the best answer for compatibility and performance reasons.

---

### Post by sxmaxchine on 2010-03-05
i think it would be great to use ubuntu in the office but not many people have heard of ubuntu let alone used it. although linux is great for running a server.

---

### Post by markbuntu on 2010-03-06
You can sandbox windows in virtual servers where you need to and move all the machines to linux as thin clients. This will give you the security reliability control and system administration coherence that you want and still allow room for windows users and the specific windows apps that they need.

---

### Post by RevKeltina on 2010-03-06
I would think the proprietary programs would be the biggest hurdle....at least where I work.  Not sure if the software we use even has a Linux version.  However, if you figure out how to make this work, let me know and I will send you the VP's phone number because I would be SO THERE!!!!!

---

### Post by cariboo on 2010-03-06
> **Techsnap said:**
> You could look at solutions such as likewise for your active directory. However I recommend that you you use CentOS or Debian over Ubuntu because of the stability factor. CentOS also has a long support schedule which means you won't have to be upgrading the OS on a regular basis.

An Unbuntu LTS server version has 5 years of support, why is that any different from Debian or CentOS. Don't let your dislike of the desktop version cloud your judgement.

For me a server install is setup and forget, the server gets stuck in an unused corner, it downloads and installs security updates only.

---

