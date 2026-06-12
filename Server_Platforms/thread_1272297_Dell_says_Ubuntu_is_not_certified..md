---
title: "Dell says Ubuntu is not certified."
date: 2009-09-22
forum: Server Platforms
---

### Post by mrcoulson on 2009-09-22
My Ubuntu project at work hit its first MAJOR obstacle today.  During a conference call with a Dell rep about the new web server we intend to purchase, the sales rep said, "Oh, I don't think Ubuntu is certified.  I've never heard of it."  

Okay, aside from being a little shocked that this Dell server expert had never heard of Ubuntu, I am really worried about the future of this project.  I've come to really appreciate the completeness and price of Ubuntu.  All in all, it's been fun to learn, the community is great, and the OS seems to have awesome support for whatever hardware is on the systems I've tested it on.  But if it's not "certified" by Dell, then my Linux project may have to switch to Suse and or Red Hat, both of which I am told are not as complete and not as free.

Any words of advice or solace?

Jeremy

---

### Post by stinger30au on 2009-09-22
there was a list of hardware ubuntu wored on at the ubuntu site itself and im sure there was some dell stuff listed

i just had a quick look and cant find the list, perhaps someone else might be able to chime in and find the page at ubuntu.com

---

### Post by dragos2 on 2009-09-22
> **mrcoulson said:**
> My Ubuntu project at work hit its first MAJOR obstacle today.  During a conference call with a Dell rep about the new web server we intend to purchase, the sales rep said, "Oh, I don't think Ubuntu is certified.  I've never heard of it."  

Okay, aside from being a little shocked that this Dell server expert had never heard of Ubuntu, I am really worried about the future of this project.  I've come to really appreciate the completeness and price of Ubuntu.  All in all, it's been fun to learn, the community is great, and the OS seems to have awesome support for whatever hardware is on the systems I've tested it on.  But if it's not "certified" by Dell, then my Linux project may have to switch to Suse and or Red Hat, both of which I am told are not as complete and not as free.

Any words of advice or solace?

Jeremy

As you can see it is certified by Dell
[http://webapps.ubuntu.com/certification/list/?category=Server](http://webapps.ubuntu.com/certification/list/?category=Server)

---

### Post by gombadi on 2009-09-22
> 
As you can see it is certified by Dell
[http://webapps.ubuntu.com/certificat...ategory=Server](http://webapps.ubuntu.com/certificat...ategory=Server)


And if you follow the link you can end up on this page -

[http://www.ubuntu.com/dell](http://www.ubuntu.com/dell)

with a paragraph -

> 
Certified Systems

Working closely with Dell's engineering team to pre-install Ubuntu, Canonical has fully tested and certified a range of notebook and desktop systems from Dell. These certified solutions are fully supported by the Canonical Support Hub based in North America, offering a choice of support options for your particular needs. 


After just having purchased 7 Dell R710 I would also like them to be certified by Dell for running Ubuntu but RH and SUSE are the only certified options available so we went Centos :-)

---

### Post by ukripper on 2009-09-22
> **mrcoulson said:**
> My Ubuntu project at work hit its first MAJOR obstacle today.  During a conference call with a Dell rep about the new web server we intend to purchase, the sales rep said, "Oh, I don't think Ubuntu is certified.  I've never heard of it."  

Okay, aside from being a little shocked that this Dell server expert had never heard of Ubuntu, I am really worried about the future of this project.  I've come to really appreciate the completeness and price of Ubuntu.  All in all, it's been fun to learn, the community is great, and the OS seems to have awesome support for whatever hardware is on the systems I've tested it on.  But if it's not "certified" by Dell, then my Linux project may have to switch to Suse and or Red Hat, both of which I am told are not as complete and not as free.

Any words of advice or solace?

Jeremy

you can always go CENTOS which is fully open source and free and build upon redhat . - [http://www.centos.org/](http://www.centos.org/)

> What is CentOS?
CentOS is an Enterprise Linux distribution based on the freely available sources from Red Hat Enterprise Linux. Each CentOS version is supported for 7 years (by means of security updates). A new CentOS version is released every 2 years and each CentOS version is periodically updated (roughly every 6 months) to support newer hardware. This results in a secure, low-maintenance, reliable, predictable and reproducible Linux environment.




-------------------------

---

### Post by slakkie on 2009-09-22
> **mrcoulson said:**
> My Ubuntu project at work hit its first MAJOR obstacle today.  During a conference call with a Dell rep about the new web server we intend to purchase, the sales rep said, "Oh, I don't think Ubuntu is certified.  I've never heard of it."  

Okay, aside from being a little shocked that this Dell server expert had never heard of Ubuntu, I am really worried about the future of this project.  I've come to really appreciate the completeness and price of Ubuntu.  All in all, it's been fun to learn, the community is great, and the OS seems to have awesome support for whatever hardware is on the systems I've tested it on.  But if it's not "certified" by Dell, then my Linux project may have to switch to Suse and or Red Hat, both of which I am told are not as complete and not as free.

Any words of advice or solace?

Jeremy

RHEL an Suse have their free counterparts: Fedora and OpenSuse. RHEL and Suse are the commercial vendors behind these two commercial and free Linux distro's.

---

### Post by mrcoulson on 2009-09-22
> **gombadi said:**
> And if you follow the link you can end up on this page -

[http://www.ubuntu.com/dell](http://www.ubuntu.com/dell)

with a paragraph -



After just having purchased 7 Dell R710 I would also like them to be certified by Dell for running Ubuntu but RH and SUSE are the only certified options available so we went Centos :-)
Right, those links seem to be for specific server models and for desktops.  

CentOS?  Will my experience between that Ubuntu be quite similar?  I'd hate to have to re-learn how to do everything in a new version.  For example, will I be able to implement SSH security and SFTP and LAMP all the same?

Jeremy

---

### Post by dragos2 on 2009-09-22
> **mrcoulson said:**
> Right, those links seem to be for specific server models and for desktops.  

CentOS?  Will my experience between that Ubuntu be quite similar?  I'd hate to have to re-learn how to do everything in a new version.  For example, will I be able to implement SSH security and SFTP and LAMP all the same?

Jeremy

Stay with Ubuntu. CentOs is community driven. Ubuntu has paid people who
carefully update the kernel, maintain the packages and very important well
tested.

---

### Post by ugm6hr on 2009-09-22
Why does it matter if it is certified?

Linux compatibility is generally kernel dependent for most servers, so there should be no problem with using Ubuntu.

If it is important, choose a vendor that will certify for Ubuntu; I think HP certify for Ubuntu.

---

### Post by Paddy Landau on 2009-10-02
> **ugm6hr said:**
> Why does it matter if it is certified?
Look how well Microsoft has done with Windows and its certification. People get a PC and expect Windows to work on it. No one got fired for buying Windows. It helps give Windows that certain cachet.

I'd love the same for Ubuntu. Imagine if, in the shops, you started seeing, "Certified for Ubuntu". What effect would that have on people!

I think that Canonical would do very well to start pushing certification, not just having a few systems certified on the website. To market the paid-for options and pay for the certification, Canonical could offer starter support packages, either free or heavily discounted for (say) 30 days along with certified hardware.

---

### Post by mrcoulson on 2009-10-02
I don't know if it really matters.  It may have some bearing on our support.  We have to buy from Dell because they're on state contract and it's super-hard to make the case that something else is a better deal because of some of the prices we are able to get from Dell.

Jeremy

---

### Post by karlson on 2009-10-02
> **mrcoulson said:**
> I don't know if it really matters.  It may have some bearing on our support.  We have to buy from Dell because they're on state contract and it's super-hard to make the case that something else is a better deal because of some of the prices we are able to get from Dell.

Jeremy

Other then calling Dell and yelling at them if the software breaks what do you intend to use the support for?

If the hardware breaks your support will still be there.  If your software has a problem Dell will probably be less useful then the forum you're posting to.  Be it Ubuntu, RedHat, SuSe or Microsoft you're running.  The only thing that you be using that requires certification would be internal hardware monitoring tools which you can do without, simply because you will have hard time installing them.

---

### Post by Vegan on 2009-10-02
I have installed Ubuntu on a range of refurbished machines and I have had few problems. NVIDIA gets nagged for closed source video drivers etc.

The latest models may lack hardware support for certain devices.

Linux is slightly behind the curve.

---

### Post by tgalati4 on 2009-10-02
Server hardware that has to run 24/7 requires some testing with the operating system to ensure it works.  If you buy a Dell server and put Ubuntu server edition on it, chances are it will work.  It's not certified by Dell, because they haven't tested it.

Depending on how mission-critical your project is, you may have to do the testing yourself to convince management that you have a reliable system.  It will take some time which will impact your development schedule.

---

