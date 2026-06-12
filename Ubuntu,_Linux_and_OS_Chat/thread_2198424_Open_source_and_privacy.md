---
title: "Open source and privacy"
date: 2014-01-08
forum: Ubuntu, Linux and OS Chat
---

### Post by fmv1992 on 2014-01-08
Dear all,
This is my first post in this awesome community. First of all I would like to thank to the massive troubleshooting that I already had with some others posts that I found on google about ubuntu. I tried ubuntu 13.10, did not like that much, now I'm using Lubuntu and I love it!
I have an array of questions that emerge in the context of privacy, the PRISM scandal, NSA etc.
1) So I was told that open source can be safer than proprietary code. The reasoning is that open source can be thoroughly reviewed and thus is less likely to have a backdoor inserted. I was looking for the linux source code, and some post redirected me to this link:
[https://www.kernel.org/](https://www.kernel.org/)
Is that correct? I "unzipped" the file and got a list of folders and files but no "main" part of the code.
2) I use a bunch of open source programs (e.g.: keepassx, Lubuntu, firefox, libreoffice, etc) and even though I have some experience with C language and bash, I am unable to review the whole code myself. And I was wondering if there is a community that in some way certifies that those programs work as they claim they do and do not mis-behave. So far open source can be peer reviewed but I did not reviewed the code myself nor have I heard of a group that do that.
Kind regards!

---

### Post by mörgæs on 2014-01-08
Hi, welcome to the fora.

It's unlikely that the Linux kernel has a backdoor like [_NSAKEY]("http://en.wikipedia.org/wiki/NSAKEY") but the main problem regarding privacy is not what goes on in the operative system. The problem is information transferred to and from your computer which can be wiretapped.

---

### Post by Dave_L on 2014-01-08
If you interested in the source code, here are a few references:

Tour of the Linux kernel source
[http://www.tldp.org/LDP/khg/HyperNews/get/tour/tour.html](http://www.tldp.org/LDP/khg/HyperNews/get/tour/tour.html)

The Linux Kernel
[http://www.tldp.org/LDP/tlk/tlk.html](http://www.tldp.org/LDP/tlk/tlk.html)

Get Source Code for any Linux Command
[http://www.thegeekstuff.com/2010/02/get-source-code-for-any-linux-command/](http://www.thegeekstuff.com/2010/02/get-source-code-for-any-linux-command/)

---

### Post by grahammechanical on 2014-01-09
I think that because Linux is developed by a community of people, who do not always agree with one another then it is very unlikely that any "backdoors" in the code base could be kept secret. We would have heard about it years ago and I think that if it happened then it would have brought the development of Linux to a full stop. 

The problem of not knowing if an application can be trusted not to mis-behave is a different issue. If we download and install applications from web sites, then we put ourselves a risk. This is why in Ubuntu we are sometimes informed that the code is from an untrusted source. We then take the responsibility for installing the code.

Applications in the Software Centre are code audited to determine that they do not do anything malicious. This is why it can take a long time to get an application accepted in the software centre catalogue.

A different approach is being taking with the Ubuntu Touch mobile platform. Application developers can use a Ubuntu SDK which includes a simple one click packaging method called Click packaging. There is also a simple and easy way of submitting the application for approval with the application being approved in minutes. This is based upon a requirement for the developer to list in a "manifest" all the authorisations that the code will require. If the code is not going to do anything nasty with those authorisations it will be approved and an AppArmor profile will be created that restricts the application to those privileges listed in the manifest. The app will not be allowed to do anything it is not supposed to do.

There is another level of protection. On the mobile platform apps will run in a sandbox. They will be prevented from going outside their declared operations. Over the next year we will see the Ubuntu mobile code base merged (converged) with the desktop code base so that there is one Ubuntu code base. So, much of the work done on Ubuntu Touch for mobile devices will come to the Ubuntu desktop.

Regards.

---

### Post by buzzingrobot on 2014-01-09
> **mörgæs said:**
> ... the main problem regarding privacy is not what goes on in the operative system. The problem is information transferred to and from your computer which can be wiretapped.

That's really important to remember.

The internet is, essentially, a public plain-text arena.  The web's original conception was as a platform for academics. No one envisioned a few billion people using it to store and transfer important personal and, potentially, confidential information.

We can use encryption, of course.  But, that's something of a pain and, in any case, can't be expected to provide a solution for mainstream users.

For the most part, privacy here depends on other people choosing not to look at the data that traverse/collect on their servers as by-products of  routine operations. 

If I had lived in a tiny village several centuries ago, my activities would be open and visible to everyone else in the village. If I wanted to keep something private, I'd need to keep it in my house. Today, while it's a cliche, the net really has made the globe something of a planet-wide village.  Using it is equivalent to "going out in public".

---

### Post by monkeybrain20122 on 2014-01-09
My view is that privacy is a matter of principle, therefore the only way to safeguard it would be try to change govt's practice through the law and democratic oversight. 

On an individual level there are people trying to use encrypted mail service and what not to evade surveillance  and all of that only make them look more suspicious and stand out as a result. As an analogy, if you don't want to live in a police state then you have to have laws to limit the power of the police and surveillance, rather than trying to hide from the police. By trying to hide you act abnormally and only draw attentions to yourself. So while they may not be able to read encrypted messages but they would know who are using encryption, and that in itself is a cause of suspicion. Since there are people doing illegal activities through some encrypted networks (child porn and what not) , users  of those networks may have actually a higher chance to be noticed by the authority. Therefore I read that some high profile privacy activist actually uses gmail as it is the least likely to draw attentions(forgot his name now) My 2 cents.

---

### Post by fmv1992 on 2014-01-09
1) > the main problem regarding privacy is not what goes on in the operative  system. The problem is information transferred to and from your  computer which can be wiretapped.
I am aware of that. But my OS (and other software) communicates via internet to get updates and so on. How could I know these connections are secure and cannot be subverted (considering that they are not malicious since their inception)?
2) Thanks, Dave_L, I'll sure take a look on those links. 
3) > The problem of not knowing if an application can be trusted not to mis-behave is a different issue. [...] Applications in the Software Centre are code audited to determine that they do not do anything malicious.
Where can I double check that? So every application that I get using the "lubuntu-software-center" has its code reviewed?
4) > The internet is, essentially, a public plain-text arena.  The web's  original conception was as a platform for academics. No one envisioned a  few billion people using it to store and transfer important personal  and, potentially, confidential information. We can use encryption, of course [...].
For web-surfing I know you can use TOR to anonimize yourself, and encryption to guarantee data integrity and privacy. But how about those non-TOR connections that software do to update and upgrade?
5) Since years I hear that Linux and other open source programs are peer reviewed (and thus safer) and now I'm trying to get deeper in this after I found out that cryptocat (open source) had a serious flaw and so far I could not google simple answers... Is there any community that dedicates itself to code review software and label it as "secure" or "insecure"?

---

### Post by Dave_L on 2014-01-09
If you want to be paranoid:

How do we know that some of the most trusted kernel and application developers are not secretly on the payroll of a goverment agency? The government could be spending a billion dollars a year to add very subtle security flaws that only they know how to exploit.

---

### Post by buzzingrobot on 2014-01-09
> **monkeybrain20122 said:**
> My view is that privacy is a matter of principle, therefore the only way to safeguard it would be try to change govt's practice through the law and democratic oversight... there are people trying to use encrypted mail service and what not to evade surveillance  and all of that only make them look more suspicious and stand out...

Different people have different, and conflicting, views of what they want to keep private. Protecting what one group asserts as its privacy interests via legislation inevitably ignores or infringes on areas other people contend are *their* privacy rights.

Then, there are varying levels of concern about behaviors.  For example. some people get very agitated about widespread CCTV use.  I don't; the presence of cameras isn't going to change my behavior.  I think they are legitimate and useful tools, as are speed limit and other traffic cameras.  So, legislation that seeks to address the concern of people who see the cameras as a privacy issue may displease people like me.

If you use something that is an obvious venue for criminal activity, then you risk being surveilled along with the criminals. If that bothers you,  don't use it.

(Meanwhile, it's naive to think security and intelligence services won't try to break every encryption scheme they come across. The public and elected will demand that every time it decides people died because the killers used encryption.)

In the end, the net is public and would not work if it were not.  If we want something kept private, don't put it on public view.

---

### Post by lykwydchykyn on 2014-01-09
Just because something is open source does NOT mean the code is audited.  However, a project the size of the Linux kernel is getting looked at by a lot of people from a lot of sectors (industry, governments, academia, etc.) all over the world.  And there are projects to audit some of these things independently, for example there's been a story in the news recently about an independent audit of the Xorg code (which found a frightening amount of flaws, but also prompted the fixing of those flaws).

If you want 100% assurance of security and privacy, you're looking at the question a little wrong, IMHO.  You can't have this unless you build every bit of it from whole cloth or study every line of code.  The linux kernel (which is hosted at kernel.org, you were told correctly) is almost *sixteen million* lines of C code.  Good luck auditing all that, and that's only the kernel.

You have to look at this as a question of managing risk and choosing the least risky option.  

You can't make an absolute blanket statement about all the code available in the software center; even if Canonical audits the code in the "main" repo, the "universe" stuff is community-packaged and mostly comes straight from Debian Unstable/Experimental.  

What using open source stuff gives you is a level of accountability.  Is it possible for backdoors/malware to get into the software repos?  Certainly, but it would require a very clever hidden bit of code and the combined cooperation of several people from several different organizations (Upstream code community, Debian packager, Ubuntu packager, etc).  This is far less likely than convincing one proprietary software company to insert code into its binary releases.

---

### Post by fmv1992 on 2014-01-09
Guys I do appreciate all of the answers,
and I do agree with you, [**[COLOR=#000000]lykwydchykyn[/COLOR]**]("http://ubuntuforums.org/member.php?u=603141"). I know that if you don't write the code yourself then you are taking a risk. What I would like to do is getting more deeper about the code reviewing. So I assume there is a community for that and something more concrete than > a project the size of the Linux kernel is getting looked at by a lot of people from a lot of sectors. This is the thing that I heard/read all my life and now I would like to certificate that this people do exist, or a place with some sort of organization and publishing about code reviewing mainstream programs.

---

