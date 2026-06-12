---
title: "Mono killed PHP5"
date: 2008-10-28
forum: Server Platforms
---

### Post by Vegan on 2008-10-28
After installing mono on my server, PHP5 stopped working. Now when I open the phpBB3 forum, the browser wants to save the page rather than render.

Tried reinstalling no joy, thoughts?

---

### Post by cdenley on 2008-10-28
In hardy, the mono module depended on the threaded version of apache while the php module depended on the prefork version. You had to choose between php and mono. This appears to be fixed in intrepid.

[http://changelogs.ubuntu.com/changelogs/pool/universe/m/mod-mono/mod-mono_1.9-1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/m/mod-mono/mod-mono_1.9-1/changelog)
> 
mod-mono (1.9-1) unstable; urgency=low

  * New upstream version.
  * Add Jo Shields to Uploaders.
  * Integrate changes from latest NMU (Closes: #457109, #472847 #486605,
    #487069). Thanks to Christian Perrier.
  * Bump standards version to 3.8.0 (no changes needed).
  [B]* Prefork Apache isn't as broken as some people thought. Dependency 
    lowered to apache2.2-common only, so any apache MPM can be chosen[/B].

 -- Jo Shields <directhex@apebox.org>  Fri, 4 Jul 2008 08:45:53 +0100



---

### Post by Vegan on 2008-10-28
That is fundamentally wrong, file.php can be rendered with PHP and file.asp can be rendered with something else. So how do it fix my forums?

My goal was to have some sites based on PHP and be able to run run others that came from a Windows server that as ASPX based so I can host all comers.

---

### Post by cdenley on 2008-10-28
> **Vegan said:**
> That is fundamentally wrong, file.php can be rendered with PHP and file.asp can be rendered with something else. So how do it fix my forums?

You upgrade to intrepid (I think it will be released in a few days), then install whichever module you are currently missing. In hardy, you can't have both the php5 module and mono module installed, because as I explained before, their dependencies conflict.

[https://bugs.launchpad.net/ubuntu/+source/mod-mono/+bug/227781](https://bugs.launchpad.net/ubuntu/+source/mod-mono/+bug/227781)

---

### Post by Vegan on 2008-10-28
What is intrepid supposed to be an upgrade for? So do I have to unlink my forums for now?

---

### Post by cdenley on 2008-10-28
> **Vegan said:**
> What is intrepid supposed to be an upgrade for? So do I have to unlink my forums for now?

hardy = ubuntu 8.04
intrepid = ubuntu 8.10

I assumed you were running ubuntu, seeing as how you are posting on ubuntuforums. Intrepid is the next release of ubuntu, due out in a few days I think. It was also suggested in the bug report I found that you serve mono pages with xsp2 on a different port, then forward apache requests to xsp2 using mod_proxy.
[https://bugs.launchpad.net/ubuntu/+s...no/+bug/227781](https://bugs.launchpad.net/ubuntu/+s...no/+bug/227781)

What do you mean "unlink your forums"?

---

### Post by Vegan on 2008-10-28
I am using Ubuntu Server 8.04 LTS which I downloaded and installed a few months ago.

So is it an automatic update?

---

### Post by cdenley on 2008-10-28
> **Vegan said:**
> I am using Ubuntu Server 8.04 LTS which I downloaded and installed a few months ago.

So is it an automatic update?

Ubuntu Server does not automatically update, unless you installed a desktop environment. If you installed a desktop environment, I think you will be asked if you want to upgrade. Since hardy will be supported longer, many people won't want to upgrade.

---

### Post by Vegan on 2008-10-28
Is the a way to graunch the situation?

---

### Post by cdenley on 2008-10-28
The best way would probably be to build the package yourself, changing the dependencies.

---

### Post by Vegan on 2008-10-28
Seems to me that the crowd made a sin, thou shalt not break an existing system. I am not quite up to par with Linux yet to start fixing the core defects.

---

### Post by cdenley on 2008-10-28
> **Vegan said:**
> Seems to me that the crowd made a sin, thou shalt not break an existing system. I am not quite up to par with Linux yet to start fixing the core defects.

You broke the system when you removed the php module in order to resolve a dependency. It's not a "core defect" but a packaging dependency because the mono module was not considered stable on the prefork apache. You wouldn't have to change any code, just some packaging rules.

---

### Post by directhex on 2008-10-28
[http://directhex.mfgames.com/hardy.html](http://directhex.mfgames.com/hardy.html)

---

### Post by Vegan on 2008-10-28
I did nothing to the php5 module, I simply installed the mono-common, so that package is the problem.

So any solution to get my forums back up?

here is come stuff from /var/log/apache2/error.log

[Tue Oct 28 11:53:03 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Tue Oct 28 11:53:03 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Tue Oct 28 11:54:30 2008] [notice] Apache/2.2.8 (Ubuntu) mod_mono/1.2.5 configured -- resuming normal operations
[Tue Oct 28 11:54:30 2008] [error] Failed running '/usr/lib/mono/1.0/mod-mono-server.exe --filename /tmp/.mod_mono_server --nonstop --appconfigdir /etc/mono-server (null) (null) (null) (null) (null) (null) (null)'. Reason: Exec format error
[Tue Oct 28 11:59:39 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Oct 28 11:59:40 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Tue Oct 28 11:59:40 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Tue Oct 28 11:59:49 2008] [notice] Apache/2.2.8 (Ubuntu) mod_mono/1.2.5 configured -- resuming normal operations
[Tue Oct 28 11:59:49 2008] [error] Failed running '/usr/lib/mono/1.0/mod-mono-server.exe --filename /tmp/.mod_mono_server --nonstop --appconfigdir /etc/mono-server (null) (null) (null) (null) (null) (null) (null)'. Reason: Exec format error
[Tue Oct 28 12:23:12 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Oct 28 12:23:13 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Tue Oct 28 12:23:13 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Tue Oct 28 12:23:22 2008] [notice] Apache/2.2.8 (Ubuntu) mod_mono/1.2.5 configured -- resuming normal operations
[Tue Oct 28 12:23:23 2008] [error] Failed running '/usr/lib/mono/1.0/mod-mono-server.exe --filename /tmp/.mod_mono_server --nonstop --appconfigdir /etc/mono-server (null) (null) (null) (null) (null) (null) (null)'. Reason: Exec format error
[Tue Oct 28 12:34:48 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Oct 28 12:34:49 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Tue Oct 28 12:34:49 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Tue Oct 28 12:34:58 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations

---

### Post by directhex on 2008-10-28
> **Vegan said:**
> I did nothing to the php5 module, I simply installed the mono-common, so that package is the problem.

So any solution to get my forums back up?

here is come stuff from /var/log/apache2/error.log

[Tue Oct 28 11:53:03 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Tue Oct 28 11:53:03 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Tue Oct 28 11:54:30 2008] [notice] Apache/2.2.8 (Ubuntu) mod_mono/1.2.5 configured -- resuming normal operations
[Tue Oct 28 11:54:30 2008] [error] Failed running '/usr/lib/mono/1.0/mod-mono-server.exe --filename /tmp/.mod_mono_server --nonstop --appconfigdir /etc/mono-server (null) (null) (null) (null) (null) (null) (null)'. Reason: Exec format error
[Tue Oct 28 11:59:39 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Oct 28 11:59:40 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Tue Oct 28 11:59:40 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Tue Oct 28 11:59:49 2008] [notice] Apache/2.2.8 (Ubuntu) mod_mono/1.2.5 configured -- resuming normal operations
[Tue Oct 28 11:59:49 2008] [error] Failed running '/usr/lib/mono/1.0/mod-mono-server.exe --filename /tmp/.mod_mono_server --nonstop --appconfigdir /etc/mono-server (null) (null) (null) (null) (null) (null) (null)'. Reason: Exec format error
[Tue Oct 28 12:23:12 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Oct 28 12:23:13 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Tue Oct 28 12:23:13 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Tue Oct 28 12:23:22 2008] [notice] Apache/2.2.8 (Ubuntu) mod_mono/1.2.5 configured -- resuming normal operations
[Tue Oct 28 12:23:23 2008] [error] Failed running '/usr/lib/mono/1.0/mod-mono-server.exe --filename /tmp/.mod_mono_server --nonstop --appconfigdir /etc/mono-server (null) (null) (null) (null) (null) (null) (null)'. Reason: Exec format error
[Tue Oct 28 12:34:48 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Oct 28 12:34:49 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Tue Oct 28 12:34:49 2008] [warn] (22)Invalid argument: Failed to destroy the '/tmp/mod_mono_dashboard_default_2' shared memory dashboard
[Tue Oct 28 12:34:58 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations

Wrong.

Firstly, "mono-common" contains absolutely nothing that could even possibly cause problems. Config files and the like. Your error message cites mod_mono in several places, which is not mono-common.

Indicate precisely what you mean to say.

Secondly, as a general rule of thumb, when people tell you something with citations and bug numbers, it means they have a reasonable grounding in what's causing problems. libapache2-mod-mono Depends: apache2-mpm-worker, whereas libapache2-mod-php5 Depends apache2-mpm-prefork. It is NOT possible to install multiple mpm packages at once - installing one will remove the other.

---

### Post by Vegan on 2008-10-28
So what else do I need to do to restore my phpBB?

Maybe I should grab the beta of 8.10

Still no forum :(

---

### Post by directhex on 2008-10-29
You were already given THREE solutions. Use one of them.

1) Put libapache2-mod-php5 back, install mono-xsp2, and configure Apache to send ASP.NET page requests to the XSP server running on a different port (e.g. 8080)

2) Upgrade to 8.10. It should go gold today or tomorrow. Friday at the latest. Then reinstall libapache2-mod-php5.

3) Use unofficial packages for 8.04 which are newer & therefore have the cited bug fixed. Then reinstall libapache2-mod-php5

---

### Post by Vegan on 2008-10-29
When I installed libapache2-mod-php5 it was already there. xsp2 was new. claims to be listing on port 8082 and localhost already.

So what do I need to do to the apache2 config?

Guess I am stuck to be a database administrator again, so much for that book, no chapter on managing SQL from a console.

Well I guess downtime is up there with getting fired, now over 24hrs down.

Hopefully Ubuntu server 8.10 comes out soon.

---

### Post by directhex on 2008-10-29
> **Vegan said:**
> When I installed libapache2-mod-php5 it was already there. xsp2 was new. claims to be listing on port 8082 and localhost already.

dpkg -l apache2-mpm-\*

> So what do I need to do to the apache2 config?

Depends. Which solution do you want to use?

> Guess I am stuck to be a database administrator again, so much for that book, no chapter on managing SQL from a console.

An SQL book without a word on SQL? Really?

> Well I guess downtime is up there with getting fired, now over 24hrs down.

Melodrama, much? Perhaps the lesson here is that if you have critical production services, you should have a distinctly separate machine (e.g. a VM) to test stuff? So you don't, y'know, break the production service?

> Hopefully Ubuntu server 8.10 comes out soon.

Tomorrow, apparently. You can install it today if you like. "do-release-upgrade -d"

---

### Post by Vegan on 2008-10-29
Installing the intrepid update, will resume gnawing away at it after its done.

---

### Post by Lars Noodén on 2008-10-30
Mono appears to be just fairly untried imitations of features already found in Java.  If you're staying with LTS and need the wealth of modules available to PHP, then you'll need to forget Mono.  You might want to look into the technical and licensing problems first anyway.  

Apache Tomcat will give you Java Server Pages and not conflict with PHP.

---

### Post by Vegan on 2008-10-30
I installed intrepid 8.10 and it has cured some of my headaches. At the same time it has revealed some IE 8 beta 2 defects.

My hair is kept short to keep me pulling it out.
:guitar:

---

### Post by directhex on 2008-10-30
> **Lars Noodén said:**
> Mono appears to be just fairly untried imitations of features already found in Java.  If you're staying with LTS and need the wealth of modules available to PHP, then you'll need to forget Mono.  You might want to look into the technical and licensing problems first anyway.  

Apache Tomcat will give you Java Server Pages and not conflict with PHP.

Licensing problems? GPL and MIT/X11 are a problem for you? Fair enough, try microsoft.com/windows

---

### Post by Vegan on 2008-10-30
I have Java on the Linux box, but I am not using it at the present time. Still in the pending heap.

Trying to figure out why mono is such a headache.

Also trying to get BIND9 of the ground.

---

### Post by directhex on 2008-10-31
> **Lars Noodén said:**
> Mono appears to be just fairly untried imitations of features already found in Java.  If you're staying with LTS and need the wealth of modules available to PHP, then you'll need to forget Mono.  You might want to look into the technical and licensing problems first anyway.  

Apache Tomcat will give you Java Server Pages and not conflict with PHP.

Actually, more problems with your post. Firstly, Tomcat is a standalone server - Mono has XSP which is standalone and would not have conflicted in any way with Apache (but would have needed messing around with forwarding per-vhost configuration in Apache, much like Tomcat)

Secondly, if you think Mono provides a *subset* of Java's capabilities, then you're either misinformed or deliberately deceiving people

---

### Post by Vegan on 2008-11-12
What is tomcat good for, I already have JavaEE on the machine.

---

### Post by directhex on 2008-11-13
> **Vegan said:**
> What is tomcat good for, I already have JavaEE on the machine.

Tomcat is a standalone JSP server

Like XSP is a standalone ASP.NET server

---

### Post by Vegan on 2008-11-13
Thanks for the brief clarification. I am happy with PHP, etc, += ASP ASP.NET etc. No real desire for Java at present. Plate is plenty full now.

Thanks for helping me up the mono stuff and understanding the issues that 8.04 had that were cured with 8.10.

At present I wonder why I can't just dump everything and write a web site in C++. At least I am very competent with that language. Learning PHP etc etc etc is a real challenge.

:guitar:

---

### Post by cdenley on 2008-11-13
> **Vegan said:**
> 
At present I wonder why I can't just dump everything and write a web site in C++. At least I am very competent with that language. Learning PHP etc etc etc is a real challenge.


Isn't that what CGI is for?
```

#include <stdio.h>

int main()
{
   printf("Content-type: text/plain\n\nHello World\n");
   return 0;
}

```

Compile it, put it in /usr/lib/cgi-bin.

---

### Post by Vegan on 2008-11-14
Thanks, I am still figuring out Ubunbtu, and its nice to see that many of my ideas can come to fruition.

:guitar:

---

### Post by neighborlee on 2008-11-14
> **directhex said:**
> Licensing problems? GPL and MIT/X11 are a problem for you? Fair enough, try microsoft.com/windows

M$ is where this trumped technology came from in the first place and what mono is based on, including  the patents ( which must be downloaded from novel, which hardly makes it GPL ) ;)

If the choice is between using software derived from a convicted monopolist, known linux hater and secret deal maker with the distro peddling Mono, and using something else entirely , which one do you think most users of a free operating system would/should opt in for ?

[http://www.mail-archive.com/foundation-list@gnome.org/msg02666.html](http://www.mail-archive.com/foundation-list@gnome.org/msg02666.html)

"  The more "cool stuff" depends on Mono, the closer we get to a
situation where a Microsoft attack on Mono would put GNOME in a vice.

If these programs are important enough to deserve the term "miss out on",
then I think they should be written in another language.
  "

Yes we can! ;)

cheers
nl

---

### Post by directhex on 2008-11-14
> **neighborlee said:**
> M$ is where this trumped technology came from in the first place and what mono is based on, including  the patents ( which must be downloaded from novel, which hardly makes it GPL ) ;)

Your repeated, concentrated, and deliberate efforts to invent your own truths to people reading this forum are getting tiresome.

Nothing "must be downloaded from Novell" other than the Microsoft Media Pack addon for the Moonlight browser plugin. No such rule exists for Mono or for Moonlight itself. However, given this is a thread about ASP.NET, as you well know, discussions of Moonlight (or attempting to pretend that things applying to Moonlight addons apply to everything) are deliberate FUD.

> If the choice is between using software derived from a convicted monopolist, known linux hater and

You really don't understand this whole "they're a business" thing, do you? What is the BUSINESS INCENTIVE to kill Mono - but not other Free Software which Microsoft could claim whatever they felt like in front of a poorly educated patent judge?

If company A wants to make some new web app, they ask themselves questions like "what's easiest", "what can be hosted on the biggest number of machines", "what leverages our existing skills", etc. If company A sees that they can have their cake and eat it - by making an ASP.NET application (rather than, say, PHP) and host it anywhere, then they get their app distributed, Microsoft get a new potential customer both for server OSes and development software - and so does GNU/Linux. If they decide on ASP.NET in the absence of Mono, then they're locking themselves out of *NIX hosting (which makes up the majority of hosts on the internets), which is shooting themselves in the foot. If they decide on something like PHP, then they need to deal with the increased development costs & support costs associated with that.

The existence of Mono benefits Microsoft. It also benefits GNU/Linux. Microsoft are too smart to cut off their nose to spite their face. The "damage" they could cause Linux is significantly less than the damage they would cause to themselves, if they killed off Mono. Of course, this ties into lots of other topics that have been covered ad infinitum and ignored ad infinitum

> secret deal maker with the distro peddling Mono,

What is secret about the Novell/Microsoft deal, specifically?

> and using something else entirely , which one do you think most users of a free operating system would/should opt in for ?

Users can opt for whatever they like. They're free to do anything - including not use Mono or Mono apps. The question is "what should DEVELOPERS" use - since those are the people making worthwhile applications.

And the answer is "whatever they feel most comfortable with" - on every level.

If people feel comfortable with ASP.NET, with thousands of lines of existing work and years of existing expertise, are you really saying "go away, Linux doesn't want you, we are our own island"?

> [http://www.mail-archive.com/foundation-list@gnome.org/msg02666.html](http://www.mail-archive.com/foundation-list@gnome.org/msg02666.html)

"  The more "cool stuff" depends on Mono, the closer we get to a
situation where a Microsoft attack on Mono would put GNOME in a vice.

If these programs are important enough to deserve the term "miss out on",
then I think they should be written in another language.

[http://www.mail-archive.com/foundation-list@gnome.org/msg02729.html](http://www.mail-archive.com/foundation-list@gnome.org/msg02729.html)

"I think that's a good basic outline for the policy: there's no need
for GNOME to reject all C# programs entirely outside the core.  But I
think that when it considers them, it should not consider each one in
isolation."

Of course, completely off-topic for an ASP.NET thread.

> Yes we can! ;)

Can what? Rewrite apps in another language? They're Free Software, you're entirely welcome to port tens of thousands of lines of simple easily-followed C# to C or somesuch. Go right ahead. Or will you complain that I'm being venomous, like last time I suggested you make something happen rather than throwing stones?

---

### Post by cariboo on 2008-11-14
Does anybody here realize that Miguel de Icaza the man that created Gnome and the Gnome Foundation is also the person responsible for mono. It was Novell that signed an agreement with Microsoft, not Miguel, as a matter of fact quite a few Linux devlopers quit working for Novell when the agreement was signed.

Jim

---

### Post by directhex on 2008-11-14
> **cariboo907 said:**
> Does anybody here realize that Miguel de Icaza the man that created Gnome and the Gnome Foundation is also the person responsible for mono. It was Novell that signed an agreement with Microsoft, not Miguel, as a matter of fact quite a few Linux devlopers quit working for Novell when the agreement was signed.

Some of us.

Some of us can't separate the idea of Microsoft, Steve Ballmer, Miguel De Icaza, Novell, and Satan, as one big pile marked "the enemy"

---

### Post by Vegan on 2008-11-14
Hmmm, sure seems my request for help has taken on a life of it's own.

Sure can tell there is a schism between Microsoft et al and the free software crowd.

Keep in mind that Windows was developed for corporate users and only later was it reconfigured to make it consumer friendly.

My Linux box does not have a GUI, I use it like old mainframes of old. No problem, doesn't everybody speak DOS/VMS/JCL/MTS etc. I even have access to mainframes in case my IBM is too sluggish.

Linux is so old school it has FORTRAN, the world's first high level programming language. Microsoft's attempt at FORTRAN was such a joke that gave up on it back when DOS was all they had.

I also have COBOL available in case some work comes my way.

I have wondered about all the pesky languages that seem to surface every now and then. When I reviewed a PHP manual, I realized I was better off with C++ a tool I am competent with.

std::cout << "Doctype....." << std::endl;

I can easily access local files, or I can crack open MySQL easily with C++. C++ is so powerful it can easily outperform PHP.

When I discovered the mono project, I figured I could bring in existing web sites and host them on the IBM as is and worked on as though they were living on a Windows Server box.

ASP, ASP.NET and Silverlight are Microsoft solutions, Flash is Adobe, and PHP is come dude's project. Everybody want a piece of the action.

The web server is not a complicated piece of software, Apache2 is available for most OSes. Same for most tools.

Recently my IBM has been upgraded to 768 MB of RAM which is lots for a console machine. The RAM can be used for caching web documents.

Microsoft owns a chunk of Corel, who bought Word perfect from Novell, and I think Microsoft also is an investor in Novell as well. Then again Microsoft has many projects on the go.

While writing this I am listening to S Club 7 :guitar:

Keep in mind Microsoft coughed up with about 1 million lines of code to make the Wine project possible. Last time I looked that was a lot of code. On a good day I can crank out 50 or 100 lines of C++. Most of the time I am reading manuals galore. C++ is a very involved programming system.

My web site is the usual LAMP stack, which is orthodox Linux. Unorthodox is the mono plug-in for Apache2.

:biggrin:

---

### Post by ushimitsudoki on 2008-11-15
> **Vegan said:**
> Keep in mind Microsoft coughed up with about 1 million lines of code to make the Wine project possible. Last time I looked that was a lot of code. 


Could you provide a reference to this claim?

The only time I know of Microsoft dealing with Wine is [back in 2005]("http://news.zdnet.co.uk/software/0,1000000121,39188944,00.htm") when they specifically checked for it to raise an error in Windows Genuine Advantage when rolling it out.

---

### Post by Vegan on 2008-11-15
I know from the newswires that the code was released. About 1 million lines was used as a base for porting Win32 to Linux to make wine possible. Microsoft gave IBM code for the older Win16 to use in OS/2.

Go search it in google.

:guitar:

---

### Post by ushimitsudoki on 2008-11-15
Wow. I'm asking because there *isn't* any such thing in Google that I can find - I already searched before asking for a cite, because it's such an incredible claim.

According to WineHQ (emphasis mine):
> Wine does not require Microsoft Windows, as it is a completely free alternative implementation of the Windows API **consisting of 100% non-Microsoft code**, however Wine can optionally use native Windows DLLs if they are available. 

Also see this [IRC interview with a Wine developer]("https://wiki.kubuntu.org/MeetingLogs/openweekintrepid/Wine") where he states:
> 
(12:10:06 PM) YokoZar: sudobash: question: Is it true that Wine is built around Windows 3.11 for its emultaor like abilites?
(12:10:25 PM) YokoZar: No
(12:11:02 PM) YokoZar: Wine is 100% microsoft-free.  There is no "built around" a version of Windows
...
...

(12:14:19 PM) YokoZar: Unlike SAMBA, Microsoft doesn't help Wine in any way.  Often times that MSDN documentation is flat-out wrong as well.
(12:15:16 PM) YokoZar: We suspect that many Wine developers know the internals of how Windows functions behave better than most Microsoft developers, though Wine developers are prohibited from seeing any Microsoft code (and if you ever have, eg downloading the stolen source code on the internet a while back, you can't ever contribute to Wine)


Finally, I even went into #winehq and asked as was told "Wine has 0 MS code".

By the way, generally the burden of proof lies on the person making the claim, not the person questioning it.

---

### Post by Vegan on 2008-11-16
I forget who broke the story, but it was widely reported a few years ago that some 1 million of lines of MS code was released for some non Windows project.

The Windows CD has 1++ billion lines of code all told. Some applets like Wordpad are major projects in their own right and I have the source to it somewhere. It has to be able to open many flavors of Word and it also has relatively basic edit capabilities.

Microsoft has had 10,000s of developers cranking out code for Windows for decades. They have created a huge body of code. And that does not include the other packages like Office etc etc.

Microsoft has tons of free stuff for educational purposes. Wordpad was published to demonstrate a large scale Windows program.

:guitar:

---

### Post by cmileto on 2008-11-16
^^

[http://www.winehq.org/site/myths](http://www.winehq.org/site/myths)


Microsoft has never (and prob will never) contribute to the wine project.

---

### Post by cariboo on 2008-11-16
> Keep in mind that Windows was developed for corporate users and only later was it reconfigured to make it consumer friendly.


Windows was always a consumer OS first and for corporate users second. Vista is actually the first Windows version to have a separate Office version.

Corporations are slow to change OS versions, as once they get everything working the way they want it to, they then need to amortize the cost over several years. Here in Canada it is usually about five years until it isn't worth writing off the value of the computer and software.

Jim

---

### Post by Vegan on 2008-11-17
Early Windows was used by developers. The SDK was expensive unlike today where you can download it for free.

Novell dominated the server market with Netware which I used to use along with FreeBSD as development machines.

FreeBSD was the only 32-bit OS available in 1986 when I bought a 386-16 machine for a server as Netware only was 286 based.

When the cost of a PC fell in the late 80s consumers began to experiment with PC machines but were put off by the hard to use DOS interface.

When Windows 3 surfaced, the UAE problem frustrated everyone limiting adoption. When Windows 3.1 finally arrived then everybody came on board as the OS was stable and flakey programs no longer crashed the system.

It was not until Windows 95 that Microsoft finally cough up with a native 32-bit OS. By that time I had been using a 386 for Windows and a 486 for the FreeBSD machine.

With Windows 95 I bought a Pentium MMX 200 processor with a PCI video card. Cost a mint but the machine had the new USB ports that took 4 years before the first USB mouse came to market.

When Windows 98 came to market, it was popular as it was a solid upgrade to Windows 95.

When Windows 2000 sufaced, I bought a CD but it was not meant for consumers who Microsoft wanted to use Windows 98. Word of mouth that everything worked brought consumers to the NT bandwagon in legions.

Windows XP dealt with many issues with Windows 2000 and for the first time Microsoft introduced copy protection. That was about the time I looked into Linux distributions for the first time.

Today I use XP x64 and Ubuntu Server 8.10. I do not like Vista for many reasons mainly due to licensing to a particular machine etc.

My web box is rock stable with Ubuntu. It has 768 MB of RAM which is plenty for a console. It bet Apache2 likes it though.

:guitar:

---

