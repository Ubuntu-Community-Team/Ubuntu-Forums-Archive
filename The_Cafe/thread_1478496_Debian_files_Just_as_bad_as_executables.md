---
title: "Debian files: Just as bad as executables?"
date: 2010-05-09
forum: The Cafe
---

### Post by themarker0 on 2010-05-09
Are debian packages just as bad as executables? Once the user presses okay, i could have control (Well not me i know not enough about programming) But is the .deb and .rpm gonna be a huge security exploit?

Disclaimer. I know nearly nothing about the security done for .deb's, and .rpm's, i am asking a question, and sparking a discussion. ;)

---

### Post by Bachstelze on 2010-05-09
Yes, DEB packages allow execution of shell scripts during several steps of the installation process, and those scripts could do anything. Installing an untrusted DEB is just as bad as executing an untrusted executable.

---

### Post by Mitchell Hale on 2010-05-09
You need root to install them though.
And there are build in trusted repositories.
So not quite as bad.

---

### Post by Bachstelze on 2010-05-09
> **Mitchell Hale said:**
> You need root to install them though.

That's exactly why you should be very careful when you install one.

> **Mitchell Hale said:**
> And there are build in trusted repositories.

Not all of them are. A lot of people use third-party repositories.

---

### Post by Crunchy the Headcrab on 2010-05-09
Sometimes I wonder just how "trustworthy" the repositories are.  I don't see any reason why malware infected software couldn't be uploaded to the repositories.

---

### Post by Mitchell Hale on 2010-05-09
> **Bachstelze said:**
> That's exactly why you should be very careful when you install one.



Not all of them are. A lot of people use third-party repositories.

Right, but some windows exes don't need admin to install/run.
And you need to set up third party yourself.

---

### Post by Bachstelze on 2010-05-09
> **Crunchy the Headcrab said:**
> Sometimes I wonder just how "trustworthy" the repositories are.  I don't see any reason why malware infected software couldn't be uploaded to the repositories.

They are watched by a large number of people, so they're a bit better than DEBs downloaded from a random website, but essentially you are right, not *that much* better. Packages in Universe are maintained by people like you and me, so there is no reason to trust them blindly.

It's a bit different for Main, since packages there are advertised as officially supported by Canonical, so if malware gets uploaded there, Canonical will be held responsible, and could lose a lot in terms of image (and therefore, money), so it's less likely.

---

### Post by amauk on 2010-05-09
[http://ubuntuforums.org/showpost.php?p=8424962&postcount=13](http://ubuntuforums.org/showpost.php?p=8424962&postcount=13)

---

### Post by cariboo on 2010-05-09
If you want to see what's inside a .deb package, you can open it using file-roller, or my favorite mc, then you can check what goes where, and what scripts are run.

---

### Post by Bachstelze on 2010-05-09
> **cariboo907 said:**
> If you want to see what's inside a .deb package, you can open it using file-roller, or my favorite mc, then you can check what goes where, and what scripts are run.

This isn't really a solution, though, what if all the script does is run an executable in the package?

---

### Post by amauk on 2010-05-09
> **Bachstelze said:**
> This isn't really a solution, though, what if all the script does is run an executable in the package?
If the DEB includes opaque binaries, then take your business else where

---

### Post by RiceMonster on 2010-05-09
> **Mitchell Hale said:**
> You need root to install them though.

Doesn't matter. All it takes is people to double click it and type in their password. Yes, people will do it without thinking. It's called social engineering and it would be a common occurrence if Linux were more widely used on the desktop.

---

### Post by Bachstelze on 2010-05-09
> **amauk said:**
> If the DEB includes opaque binaries, then take your business else where

Binaries are by definition opaque, and I think most DEBs include binaries.

---

### Post by earthpigg on 2010-05-09
> **Bachstelze said:**
> This isn't really a solution, though, what if all the script does is run an executable in the package?

you are correct, it isn't the solution.

the solution is not to add untrusted repositories, and not to download/install packages from untrusted websites.

it is ultimately up to the user to decide who/what he trusts, and who/what he does not trust.

malicious software spread via .deb absolutely relies on *user error* and *social engineering*. there is no inherent flaw in the .deb package format.

while looking at ze pr0ns, for example, i've come across an apparent flash video. when you click the play button, it says "you must have the latest version of flash to play this video. would you like to download it now?" and offers adobe_flash_installer.exe for download.

that is an example social engineering - and that trick could work just as well with a .deb file. there is no weakness in .exe or .deb installers, the weakness is the user.

not that i think folks that fall for this are bad people, mind you, just distracted... either by the desire to "pimp their facebook" using "facebookpimper.exe" or by their hormones. there is also ye good ole FarmVille_automatic_farmer_setup.exe. and the thing about that one? apparently, it actually works! it will actually automate the farmville grind (*in addition* to adding the user's computer to a botnet.).

it is essential for computer users to keep their paranoia turned on at all times, no matter what other parts of their person/anatomy are similarly activated. 

the only way we will ***ever*** see the Internet become as safe a place as your local dog walking park at 2 pm is if some sort of World Government is formed and has the Force of Violence backing it (can law enforcement effectively enforce anything if they are *never* allowed to use violence? [Here for more.]("http://en.wikipedia.org/wiki/Monopoly_on_violence")). 

Otherwise, the bad guys can just move to a non-participant nation. Do you *really* think the Dictator or "President" of ________ wants to stop his citizens from stealing money from and taking over the computers of Americans, Japanese, S. Koreans, Europeans, etc, over the Internet and bringing it into his impoverished nation? Hell, he'd be more tempted to legalize it, regulate it, and tax it!

Anyways, back on topic:

there is no emergency number to call, and you are on your own. the closest thing available is your local computer repair shop, which is much like a for-profit hospital. the only way you will ever have any chance of getting your stolen assets back is if the criminal is caught and coincidentally happens to be from your nation, or one that your nation has an extradition treaty with.

Pick who you trust carefully, because you never know who has a "Get out of Jail Free" card on the good ole net and has nothing to fear.

---

### Post by amauk on 2010-05-09
> **Bachstelze said:**
> Binaries are by definition opaque, and I think most DEBs include binaries.
sorry, what I meant by "opaque binary" is a pre-complied program without the option of building from source
(a la the nvidia binary drivers, and similar)

---

### Post by Bachstelze on 2010-05-09
> **amauk said:**
> sorry, what I meant by "opaque binary" is a pre-complied program without the option of building from source
(a la the nvidia binary drivers, and similar)

This is not perfect either. There is nothing that guarantees a given executable was compiled from a given piece of source code, and even if there were, a malicious compiler could add malicious code at compile time without the user's noticing.

You might want to read Ken Thompson's Turing Award acceptance speech.

---

### Post by scrooge_74 on 2010-05-09
If you managed to install any Linux version on your equipment then you are not the average computer user and I would think you would be smart enough to know not to install any .deb you find along the way.

---

### Post by amauk on 2010-05-09
well,
distros will build all their packages from source
the point is, if you stick to the repos, security of packages is handled by your distro (and/or upstream distro - Debian -> Ubuntu)

The onus of security and package integrity is on the distro (who know what they are doing) as opposed to the user (who may not)

---

### Post by Bachstelze on 2010-05-09
> **amauk said:**
> 
The onus of security and package integrity is on the distro (who know what they are doing)

*cough* OpenSSL *cough*

---

### Post by earthpigg on 2010-05-09
> **Bachstelze said:**
> This is not perfect either. **There is nothing that guarantees a given executable was compiled from a given piece of source code**, and even if there were, a malicious compiler could add malicious code at compile time without the user's noticing.


*cough* Google Chromium Source Code -> **???** -> Google Chrome *cough*

excuse me, i must be coming down with something.

edit: wow, Bachstelze, there must be something going around. :D

---

### Post by amauk on 2010-05-09
indeed
no system is infallible to the human element
but the point still holds

Stuff in the repos will always be infinitely more "trustable" than some random deb you find on the net

---

### Post by earthpigg on 2010-05-09
> **amauk said:**
> 
Stuff in the repos will always be infinitely more "trustable" than some random deb you find on the net

ill agree to that. and it works out algebraically, too!

zero trustability * anything... is still zero!

thus, anything with any trustability at all must be infinitely more trustable.

edit: and just to clarify, i don't think Google is intentionally spreading malicious software that will destroy your computer via Google Chrome's .deb installer. I do suspect, however, that there could be *additional* spyware that is *not* present in the alleged full source code (chromium). do you consider spyware to be "malicious", if it comes from a corporation with an official corporate ethic that states "don't be evil" ? I can't answer that question for anyone but myself.

---

### Post by chillicampari on 2010-05-09
> **scrooge_74 said:**
> If you managed to install any Linux version on your equipment then you are not the average computer user and I would think you would be smart enough to know not to install any .deb you find along the way.

While not exactly the same thing as downloading an unknown .deb, this seems relevant to the convo (as far as generally over-trusting things go):

[http://ubuntuforums.org/showthread.php?t=1399789](http://ubuntuforums.org/showthread.php?t=1399789)

---

### Post by phrostbyte on 2010-05-09
There was a virus tailored for Ubuntu that was distributed as a .deb claiming to be a screensaver or something like that.

---

### Post by 3rdalbum on 2010-05-09
> **phrostbyte said:**
> There was a virus tailored for Ubuntu that was distributed as a .deb claiming to be a screensaver or something like that.

If it was claiming to be a screensaver, then it's a trojan, not a virus.

I remember that trojan. Gdebi actually lets you look at the contents of the package before you install it. You can have a look at the scripts in it and where the files will go to. An educated Linux user could look at the contents of the "screensaver" package and see the script that downloads its payload from a website and smell a rat.

What I think is a flaw is that Debian package control scripts can be in any interpreted language. They might even be allowed to be binaries, I haven't tested this though. For safety I think the control scripts should be interpreted ONLY by 'sh'. It would break a handful of packages that use Python or Perl control scripts, but it would be safer.

---

### Post by themarker0 on 2010-05-09
> **3rdalbum said:**
> If it was claiming to be a screensaver, then it's a trojan, not a virus.

I remember that trojan. Gdebi actually lets you look at the contents of the package before you install it. You can have a look at the scripts in it and where the files will go to. An educated Linux user could look at the contents of the "screensaver" package and see the script that downloads its payload from a website and smell a rat.

What I think is a flaw is that Debian package control scripts can be in any interpreted language. They might even be allowed to be binaries, I haven't tested this though. For safety I think the control scripts should be interpreted ONLY by 'sh'. It would break a handful of packages that use Python or Perl control scripts, but it would be safer.

But who actually looks at the source? What if the source is getting the file from the server?

---

### Post by 3rdalbum on 2010-05-10
> **themarker0 said:**
> But who actually looks at the source? What if the source is getting the file from the server?

If you have a healthy suspicion of random Debian packages from the web, you would look at the control scripts.

If the "screensaver" package is getting a file from a URL, that would raise alarm bells for me. There's no reason why a legitimate package would download stuff rather than put it in the package; except for things like Flash Player, but you'd expect that the URL it would 'wget' from would be [www.adobe.com](www.adobe.com).

---

### Post by WinterRain on 2010-05-10
> **Bachstelze said:**
> Yes, DEB packages allow execution of shell scripts 

Only if you allow them to. Download debs from trusted sources and don't worry. Better yet, stay with the repos.

---

### Post by Bachstelze on 2010-05-10
> **WinterRain said:**
> Only if you allow them to.

Wrong.

[http://www.debian.org/doc/debian-policy/ch-binary.html#s-maintscripts](http://www.debian.org/doc/debian-policy/ch-binary.html#s-maintscripts)

Not all maintainer scripts prompt the user. Actually, a large minority of them do.

> **WinterRain said:**
> Download debs from trusted sources and don't worry. Better yet, stay with the repos.

Can the repos be really trusted? You sound like Dolores Umbridge. "Don't worry, the Ministry is here to protect you. No evil wizard is out there..."

---

### Post by WinterRain on 2010-05-10
> **Bachstelze said:**
> 
Not all maintainer scripts prompt the user.
In my experience, I have never clicked a .deb that hasn't prompted me for my password.
> **Bachstelze said:**
> Can the repos be really trusted?
Yeah, the stock ones can be trusted.
 > **Bachstelze said:**
> You sound like Dolores Umbridge. "Don't worry, the Ministry is here to protect you. No evil wizard is out there..."
I don't appreciate this comment, and will now terminate discussions with you. I am not a noob, and am well aware of all the "evil" out there. Just because I feel the main avenues of getting software are safe, doesn't mean you should attack me. Have a nice day.

---

### Post by v1ad on 2010-05-10
in some cases the .deb files are great. for the beginner user that is just getting to know Linux these programs install quick and easy and installs all necessary files to go with it. it is basically a life saver for some.

---

### Post by WinterRain on 2010-05-10
> **v1ad said:**
> in some cases the .deb files are great. for the beginner user that is just getting to know Linux these programs install quick and easy and installs all necessary files to go with it. it is basically a life saver for some.

Exactly. Of course there will always be questionable software out there, but if you stick to the tried and true sites that have debs, Bad code won't get very far, and will most likely be reported immediately.

I never said that it was impossible for linux boxes to get "infected", but by far and large, the chances are substantially less than in windows. Sure, I could get struck by lightning, but the chances are probably a few million to one. About the same chance as getting a "virus" in linux. I like those odds for now.

---

### Post by michaeldt on 2010-05-10
There is no solution, other than inspecting each and every .deb you wish to install. There is always a compromise. 

Use a "trusted" repo and live with the fact that there may still be a small chance of something getting through. 

Use only repos maintained by canonical and the chances are even smaller but choice of software is less as well.

Ignore repos and install random .deb from the net and the risk is huge but the choice of software is as well.

At least for Linux users, we have a trusted repo where we know that someone has taken the time to compile form source (or only include binaries from the actual developer - think binary drivers) and test for nastiness. Windows users simply have to rely on the trustworthiness of the site they download from knowing that unless that site belongs to the producer of the software, all the site is doing is redistributing precompiled apps with no knowledge of how safe they are.

On the otherhand, windows users have anti-virus which can check for know malware. Since very little known malware exists for Linux, this is more difficult. 

One solution, is an app which detects "suspicious" behaviour of scripts and other apps, something which wants to make changes to system files, partitions, user info, suspicious commands etc. This would at least help to prevent something from bricking a PC. In the event a script tries to do something like this, the user could be alerted to the proposed actions/changes and the user would need to confirm them.

---

### Post by earthpigg on 2010-05-10
> **michaeldt said:**
> 
One solution, is an app which detects "suspicious" behaviour of scripts and other apps, something which wants to make changes to system files, partitions, user info, suspicious commands etc. This would at least help to prevent something from bricking a PC. In the event a script tries to do something like this, the user could be alerted to the proposed actions/changes and the user would need to confirm them.

defining "suspicious" would entail a great deal of assumptions on the part of the developer of that app. assumptions about a system's setup, when interacting with GNU/Linux users, do not generally bode well.

---

### Post by Paqman on 2010-05-10
Pretty much by definition, any prepackaged executable installer is going to be able to mess about with your system. It's not really a case of .deb, .rpm or .exe being "bad" as such. Installing any software is potentially opening a window for malware.

---

### Post by rasmus91 on 2010-05-10
> Yes, DEB packages allow execution of shell scripts during several steps of the installation process, and those scripts could do anything. Installing an untrusted DEB is just as bad as executing an untrusted executable.

And thats Exactly why its safe: Use TRUSTED software channels, no security exploits...

People shouldn't run .debs that they have randomly downloaded from some homepage...

---

### Post by 3rdalbum on 2010-05-10
> **Bachstelze said:**
> Can the repos be really trusted?

Only known, registered and proven developers and packagers can upload to Universe. The standards are very high for Ubuntu packagers and all applicants get intensely grilled before being accepted. They also have to be sponsored by another MOTU or Ubuntu developer.

The standards are even higher for people packaging and developing for Main.

In short, you can trust the Ubuntu repositories.

---

### Post by Meep3D on 2010-05-10
The question should be why does software need to run a script on install?  It should be a bunch of files and a manifest, with the OS putting the files where it deems fit and removing them on your request and when the program is run it should be run in a sandbox without direct access to the filesystem or even the users files without explicit permission.

The reasons Windows has had so many problems and has such a bad rep is from trojans exactly like have been described above.  The proposed solutions 'don't use anything outside the repo' and 'only  use built from source software' simply doesn't cut it in this day and age.  You can just about get away with that ala Apple's iPhone but not on the desktop.

It seems the movement to webapps is largely a response to this issue but the real solution should be to allow the user to treat a native app as untrusted, rather than fully trusted just as you treat websites as untrusted.

---

### Post by MarcusW on 2010-05-10
I read somewhere next RHEL will include a tool to easily make a jail for testing software. That's something I'd really like to see in Debian (and Ubuntu). Does anyone know of an easy way to do this? (including graphical programs)

---

### Post by Viva on 2010-05-10
You can't protect people from themselves. Social engineering is a threat no matter how secure an operating system is.

---

### Post by prodigy_ on 2010-05-10
I honestly don't understand the purpose of this thread. If you're paranoid and don't want to use any binaries whatsoever, switch to Gentoo or Arch. Read all sources and compile them yourself. Problem solved.

---

### Post by 3rdalbum on 2010-05-10
> **Meep3D said:**
> The question should be why does software need to run a script on install?

To turn off old versions of a service and start the new version straight away; in the case of Linux kernels the script will recompile DKMS-enabled modules and update the GRUB menu.

I'm sure people can think of other details.

Why is having a script so much more of a security flaw than being able to drop scripts into your startup sequence?

---

### Post by Bodsda on 2010-05-10
> **MarcusW said:**
> I read somewhere next RHEL will include a tool to easily make a jail for testing software. That's something I'd really like to see in Debian (and Ubuntu). Does anyone know of an easy way to do this? (including graphical programs)
 
You can, just create a chroot jail.
 
Bodsda

---

### Post by themarker0 on 2010-05-10
> **prodigy_ said:**
> I honestly don't understand the purpose of this thread. If you're paranoid and don't want to use any binaries whatsoever, switch to Gentoo or Arch. Read all sources and compile them yourself. Problem solved.

No i just read threads saying "You can't infect linux, its impossible" For once i wanted a thread saying its possible, and been done before. Also if you read the OP, you would've saw that i was asking a question first ;)

---

### Post by Paqman on 2010-05-10
> **themarker0 said:**
> No i just read threads saying "You can't infect linux, its impossible"

Who says that? Of course it's possible. If it wasn't we wouldn't need to take any security precautions at all.

---

### Post by RiceMonster on 2010-05-10
> **prodigy_ said:**
> I honestly don't understand the purpose of this thread. If you're paranoid and don't want to use any binaries whatsoever, switch to Gentoo or Arch. Read all sources and compile them yourself. Problem solved.

Arch is a binary distro. Also, you should be able to read the source and recompile any (FOSS) package on any linux distro.

---

### Post by themarker0 on 2010-05-10
> **Paqman said:**
> Who says that? Of course it's possible. If it wasn't we wouldn't need to take any security precautions at all.

Do a simple search, people say it quite often.

---

### Post by undecim on 2010-05-10
If I can convince you to install a piece of software on your computer without verifying that it's safe, then there is no hope to keeping your computer secure.

I could publish a tutorial that creates a new user with admin privileges, sets up SSH, and notifies a server of mine, and if you follow that tutorial completely, that's just as bad as me giving you a deb that does the same thing.

In other words, there is no way to secure against human stupidity.

---

### Post by themarker0 on 2010-05-10
> **undecim said:**
> If I can convince you to install a piece of software on your computer without verifying that it's safe, then there is no hope to keeping your computer secure.

I could publish a tutorial that creates a new user with admin privileges, sets up SSH, and notifies a server of mine, and if you follow that tutorial completely, that's just as bad as me giving you a deb that does the same thing.

In other words, there is no way to secure against human stupidity.

Most people i know stupid enough to get viruses on windows, don't follow tuts.

---

### Post by aysiu on 2010-05-10
> **themarker0 said:**
> Do a simple search, people say it quite often.
Then those people are wrong.

Or perhaps you're confusing "antivirus is useless" with "Linux is invincible"?

Antivirus *is* useless, but that doesn't mean Linux is invincible. Nor does it mean that any system can be immune to social engineering, since social engineering relies on tricking the *user* into compromising the system.

---

### Post by themarker0 on 2010-05-10
> **aysiu said:**
> Then those people are wrong.

Or perhaps you're confusing "antivirus is useless" with "Linux is invincible"?

Antivirus *is* useless, but that doesn't mean Linux is invincible. Nor does it mean that any system can be immune to social engineering, since social engineering relies on tricking the *user* into compromising the system.

There are ways, they'd be more annoying then the security on windows vista, but there are ways.

---

### Post by TheNessus on 2010-05-10
compiling from source and stuff like that are just as bad as well if you don't nitpick for malcode. I can't do that, it's chinese for me, so .Deb files are a godsend to me.

---

### Post by earthpigg on 2010-05-10
> **MarcusW said:**
> I read somewhere next RHEL will include a tool to easily make a jail for testing software. That's something I'd really like to see in Debian (and Ubuntu). Does anyone know of an easy way to do this? (including graphical programs)

the easiest way i can think of, if you want to stay graphical and don't want to learn a bunch of stuff would be to use remastersys -> virtualbox.

both have gui.

---

### Post by Old_Grey_Wolf on 2010-05-10
If I discovered malware in a package delivered by a trusted repository, how would I report it, and to whom?

---

### Post by Bachstelze on 2010-05-10
> **Old_Gray_Wolf said:**
> If I discovered malware in a package delivered by a trusted repository, how would I report it, and to whom?

Depends. If it's in an official Ubuntu repository, file a bug against the package in question. Otherwise, complain to the person who manages the repository.

---

### Post by doorknob60 on 2010-05-10
Well, If you download and install random DEBs the same way would would install random EXEs on Windows, it could potentially have malware (but I bet very few, if any, DEBs have malware). The big difference is most software is installed through the Ubuntu official repositores (safe), and Windows has nothing like that.

---

### Post by Paqman on 2010-05-11
> **themarker0 said:**
> Do a simple search, people say it quite often.

Not anyone that actually knows what they're talking about.

Linux is definitely theoretically vulnerable to malware, we just don't have any active threats spreading in the wild. That's not to say someone couldn't release one tomorrow.

---

### Post by MarcusW on 2010-05-11
> **earthpigg said:**
> the easiest way i can think of, if you want to stay graphical and don't want to learn a bunch of stuff would be to use remastersys -> virtualbox.

both have gui.

Yeah that's true, but I wouldn't really call it easy. (if you just want to quickly test a program if it is safe before you install it)

---

