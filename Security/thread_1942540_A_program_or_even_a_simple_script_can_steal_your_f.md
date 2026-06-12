---
title: "A program or even a simple script can steal your firefox passwords"
date: 2012-03-17
forum: Security
---

### Post by Ol'manScratch on 2012-03-17
Hi
I just spotted this on another post and it got me wondering if it is accurate.

"A program or even a simple script **can steal your firefox passwords and other important stuff even in Ubuntu Linux _*without root password*_**, so _don't run things blindly!_"

I run my system through an ActionTec DSL modem with a wireless gateway (not set up for wireless)
I have been having several small issues with my system that made me wonder about Ubuntu virus worries.
I've been using Ubuntu for a couple of years, but have not become proficient with it beyond the basic of doing what I want it to do.
Most of the alarming problems I'm having are since upgrading to Oneric.
I have mouse problems (covered in a separate post)
Suddenly my system goes into hibernation after a while, but I did not set it to do that.
The monitor will suddenly fade an go dark even when I am actively using it, but recovers when if I hit the space bar.
When I want to open more than 2 windows, using the ALT/TAB will only allow 1 window to show at a time. Is there a way to go back to when all open windows were shown at the bottom of the screen?
Also, when I use personal font settings they do not always work. When I set them to "allow sites to choose their own fonts" that setting does not usually work right.

 I thought I was installing a stable version of Oneric that would work like all the previous releases, but it does not seem to be the case.
So the question is: Is Ubuntu Oneric more susceptible to viruses than I previously though and should I change to a better DSL modem and add an anti-virus program?
Thanks

---

### Post by jerome1232 on 2012-03-17
> **Ol'manScratch said:**
> 
 I thought I was installing a stable version of Oneric that would work like all the previous releases, but it does not seem to be the case.
So the question is: Is Ubuntu Oneric more susceptible to viruses than I previously though and should I change to a better DSL modem and add an anti-virus program?
Thanks

What does your modem have to do with viruses?

A script taking information out of firefox is a) not a virus and b) a firefox flaw, afaik no browser automatically encrypts your login information it stores so this is technically true of all browsers, on all operating systems.

If your interesting in security on Ubuntu check out the stickies in the security discussions. [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by uRock on 2012-03-17
Moved to *Security Discussions*.

---

### Post by Dangertux on 2012-03-17
Okay check it out. Yes, firefox stores your stored usernames and passwords - it does so in a sqlite database, that is relatively easy to put back together.

That being said, what you're experiencing is absolutely not indicative of anything other than hardware comptaibility issues. As already stated, your modem and anti-virus software (to a lesser extent) have almost no influence over Ubuntu 11.10's overall security posture, though if you want the "most secure" you should always opt for the LTS releases, as development releases are not targeted to be production ready systems, and will logically receive less scrutiny when it comes to overall security standing.

Hope this helps.

---

### Post by Ms. Daisy on 2012-03-17
It seems like maybe you would benefit from reading the [Basic Security Wiki]("https://wiki.ubuntu.com/BasicSecurity").

In particular, it talks about securing your browser.  Sounds like you would be interested in that section. And there's information about securing your router which may also help you out.

---

