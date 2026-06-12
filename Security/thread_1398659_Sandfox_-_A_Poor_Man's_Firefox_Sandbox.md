---
title: "Sandfox - A Poor Man's Firefox Sandbox"
date: 2010-02-04
forum: Security
---

### Post by IgnorantGuru on 2010-02-04
So Fedora 12 has [a convenient sandbox](http://www.h-online.com/open/Fedora-12-demonstrates-sandbox-for-desktop-applications--/news/114298) for running Firefox and other apps.  Chrome runs sandboxed.  And Windows 7 can even run IE sandboxed (allegedly).  But in trying to find an easy, ready-to-go sandbox for Ubuntu and Arch I didn't find anything.  Given Firefox's use of the exploit-ridden Flash, Java, and third-party plugins, I think this is an important ability.

For those who aren't familiar, a sandbox is a way of running an app in a way that limits its access to the system resources.  For example, Firefox running in a sandbox would only be able to access a limited subset of the filesystem - only the folders you include in the sandbox.  This way any processes Firefox uses, such as Java, Flash, and plugins, are also limited.

There are full (over-)blown solutions for this, such as AppArmor, SELinux (which is how Fedora apparently accomplishes it), and others.  But none ready to go with no configuration.  (Plus, I personally don't put a lot of trust in Novell or SELinux.)  And I trust Google with my private data as much as I trust Microsoft, so Chrome is nothing I want anything to do with.  The lack of options led me to develop Sandfox, which is designed to be easy to use and also flexible.

In the easy department, you can install Sandfox and have Firefox running in a sandbox with one command:
```
sudo sandfox firefox
```

In the flexible department, any app can be run sandboxed, either sharing a single sandbox or one for each program, based on profiles you can create.

Sandbox is written in pure bash and uses only core Linux commands to create a chroot jail for Firefox.  I wrote this primarily for my own use (and I'm writing this post from a sandboxed Firefox) but I'm sharing it because I think it fills a niche for a ready-to-go app sandbox.  I'll let you review the website for the additional details.  If you have any questions feel free to ask.
[http://igurublog.wordpress.com/downloads/script-sandfox/](http://igurublog.wordpress.com/downloads/script-sandfox/)

```
sandfox --help

Usage: sandfox [OPTIONS] [COMMAND [ARG]...]
Runs COMMAND as a normal user within a chroot jail sandbox with limited
access to the filesystem.  Supports profiles for apps and includes a default
Firefox profile. Must be run as root when creating sandbox.  Examples:
 sudo sandfox firefox                    # Runs Firefox in a sandbox
 sudo sandfox bash                       # Shell to explore a sandbox
OPTIONS:
--bindro TARGET           Include TARGET (a file or folder) in the sandbox
                            bind-mounting it as a read-only filesystem
--bind TARGET             Include TARGET (a file or folder) in the sandbox
                            with same ownership and permissions when possible
--copy TARGET             Place a disposable copy of TARGET (a file or folder)
                            in the sandbox
--hide TARGET             Include TARGET (a file or folder) in the sandbox
                            by bind-mounting an empty file or folder onto it
                            Effectively hides the real TARGET from the sandbox
                            Also provides a writable dummy folder
--profile PROFILE         Load PROFILE (a profile name or pathname).  By
                            default profiles are stored in /etc/sandfox
--make                    Force creation or update of a sandbox (make is
                            implied if you specify binds or profiles)
--sandbox NAME            Specify name of sandbox to use, create, or update
--close NAME              Unmount and remove sandbox NAME
--closeall                Unmount and remove ALL sandboxes
--status                  Show the status of all current sandboxes
--shell                   Run COMMAND in a shell and wait.  Requires root.
                            (bash is always run in a shell)
--user USERNAME           Run command as USER in the sandbox - useful if
                            auto-detection does not work or to override
--profilefolder FOLDER    Use FOLDER instead of the default profile folder
                            IMPORTANT: should be root owned & write-protected
--logfile LOGFILE         Also append messages to LOGFILE.  sandfox daemons
                            will also update this file provided it is
                            accessible from within the sandbox.
--verbose                 Provide detailed feedback
--quiet                   Minimize output messages
NOTES: OPTIONS must precede COMMAND; you can also use OPTION=VALUE; binds are
processed in this order: bindro bind copy hide; missing binds are ignored; if
a profile for COMMAND exists it will be automatically loaded; default profile
is always loaded; profiles may contain any options valid on the command line;
if COMMAND is omitted, a sandbox will be created for use.
```

---

### Post by bodhi.zazen on 2010-02-04
Congrats for all that work.

I believe the Fedora sandbox you are referring to uses selinux to sandbox apps and it is not fully functional as of yet (assuming we are talking the same sandbox here).

[http://danwalsh.livejournal.com/31146.html](http://danwalsh.livejournal.com/31146.html)

The equivalent would be to use Apparmor, and starting with Ubuntu 9.10 there is a default apparmor profile for firefox.

I would trust selinux and apparmor long before I trusted a chroot jail (not that chroot jails are bad, just there are not that hard to break out of either).

Another option would be to use LXC, and ssh in with Xepher. LXC are very similar to chroot, but much improved in terms of security.

---

### Post by IgnorantGuru on 2010-02-04
> **bodhi.zazen said:**
> Congrats for all that work.

Thanks - I'm learning a lot with it.

> The equivalent would be to use Apparmor, and starting with Ubuntu 9.10 there is a default apparmor profile for firefox.

Right - personally I would not use AppArmor or SELinux.  If you don't mind state- and corporate-sponsored backdoors they will stop script kiddies, I'm sure.  They're probably good for the enterprise level.  But if I wanted a huge trojan I'd run Windows.  :)  Given the origins and affiliations of Novell and SELinux, it's a bit like having the fox guarding the chickens.  But that's just me.  There are other full-blown solutions I would use before I would use those.

> I would trust selinux and apparmor long before I trusted a chroot jail (not that chroot jails are bad, just there are not that hard to break out of either).

From my research into it, and from speaking with people more knowledgeable than myself, chroot jails aren't that hard to break out of if you have root running in them.  In Sandfox's case, only a normal user runs in a root-enforced chroot jail, which is quite secure.  I'll owe you a nickel if you can show me how to break out of a Sandfox sandbox.  :)

But I'm not suggesting this is intended to replace the likes of SELinux, etc., which also handle network access and other issues.  This is just a filesystem jail that has the advantage of using core Linux commands.  Perhaps it will get people more interested in sandbox potentials, and then they'll move on to greater things.  Mainly, this provides a pretty tough layer between the app and the filesystem - should be as tough as any use of root.  And without any dependencies on huge libraries of allegedly peer-reviewed code.

Another advantage to this approach is it uses virtually no system resources - Firefox will run at full speed.  (In fact, it could be my imagination but it seems to run faster.)  Also, it has the ability to create a disposable copy of your .mozilla folder in the sandbox and destroy it when the sandbox is closed.

> Another option would be to use LXC, and ssh in with Xepher. LXC are very similar to chroot, but much improved in terms of security.

I looked at LXC briefly but one problem I have with such solutions is that they don't seem to follow the Keep It Simple approach.  But I'm going to look at that some more.

Thanks for your comments and suggestions.

---

### Post by bodhi.zazen on 2010-02-04
Well, both SELinux and Apparmor are open source, and no back door has yet been identified. Apparmor is no longer maintained by Novell.

I used to trust chroot jails, but once you learn to break out you will not trust them as much as you do now. This is why people develop alternates such as LXC, OpenVZ, Xen, and BSD jails.

Other then that, this is not a proof of concept forums (in terms of breaking out of jails), but ask those you trust, who are more knowledgeable then you, to explain how to break out of chroot jails.

In terms of simplicity, 

```
sudo aa-enforce firefox
``` done . Right back at you, I will give you a nickle if you can break out of the firefox apparmor profile. I will give you dime if you can demonstrate a back door to either selinux or apparmor.

Now you may wish to change some of the settings in the default profile, that is up to you.

If you wish to remove .mozilla, take a look at shread or dd.

Take care with your argument re: "root confined". With a default installation all system files are root confined, so, at the end of the day, how is it your confinement is any better then the defaults ? I would caution that it is not. The ability to alter system files implies root access, which implies root access within your chroot, which implies escape. This is the problem that tools such as selinux and apparmor are trying to address, restricting even root.

LXC is not a viable alternate yet if you want simple, give the project some time to develop the user tools and it likely will be.

I am not trying to discourage you, but, if you get over your bias re: aa and selinux you may find them to be very viable and secure options.

I am also cautioning you that your confinement is not as strong as you think it is. An exploit that allows one to run arbitrary code implies root access and you have not confined root.

---

### Post by IgnorantGuru on 2010-02-04
> Take care with your argument re: "root confined". With a default installation all system files are root confined, so, at the end of the day, how is it your confinement is any better then the defaults ?

It is not better than the defaults, it is merely as good as them.  Sandfox doesn't aim to address protecting apps as much as it aims to address protecting user's data.  I discuss this in my article _*[Fear Not Root](http://igurublog.wordpress.com/2010/01/16/fear-not-root/)*_ if you're interested.  Simply put, root may protect system files (the least valuable and most easily replaced data on your system), but it does nothing for most PC user's data, nor does it stop arbitrary code from running.

Sandfox's design aims to use the power of root to protect more of that data.

> I am not trying to discourage you, but, if you get over your bias re: aa and selinux you may find them to be very viable and secure options.

I simply don't trust their origins.  I can't demonstrate a backdoor, but I'll bet if I reviewed the million lines of code I could find one.  It would then be labeled a 'mistake' and corrected.  It's called plausible deniability.

At any rate, that's just my personal, irrational take on it as a card-carrying skeptic of anything corporate built and NSA influenced.  These are the people whose business it is to steal.  I don't think their primary concern is your security.  ;)

But I'm not suggesting Sandfox is military-grade security.  It's more like making files owned by root and inaccessible as far as some apps are concerned.

> An exploit that allows one to run arbitrary code implies root access and you have not confined root.

Not at all.  It does not require root access to run arbitrary code in Linux.  Any user can compose or download software and run it.  You may need root to install it, but not to run it.  Like many devs, you are thinking that the most valuable data are the system files.  I consider that the least valuable data on a PC.

---

### Post by IgnorantGuru on 2010-02-04
At any rate, I appreciate the dialog with bodhi.zazen - he brought up some good points to consider.  But some of that went far off-topic in terms of what Sandfox does, so let me just clarify what Sandfox does and does not do.

Imagine if you didn't trust Firefox, Java, Flash, and 3rd party plugins, so before you ran it, you logged in as root and made some folders root-owned and inaccessible.  Then you ran the program.  You have effectively used the power of the root account to create a sandbox for Firefox (and every other app running as a normal user on your entire system).  Since Firefox is running with your user privileges, unless it has an exploit to get root privileges, it can't access some files.  This mechanism is at the core of how Linux limits users.

That is really all Sandfox does - it just does it in a more convenient way.  Instead of sandboxing all apps at once, it just sandboxes the apps you choose.  But the rest is about the same - root is used to protect your data.

As far as jail-breaking, most of those techniques revolve around getting root out of a jail.  While I am not an expert on jail-breaking, I have reviewed the techniques from various sources, and they simply don't work as a normal user.  You are welcome to try them in a Sandfox sandbox, but since you don't have root, it will be basically as difficult as getting root access on your Linux system when you don't have the root password.  In fact it will be more difficult, since you won't have access to the whole filesystem - you won't be able to run su, for example, even if you DO have the root password.  Sandfox just uses the already-established root mechanism of Linux, extending it to protect your user data, which Linux generally does a poor job of.  I discuss this in [Fear Not Root](http://igurublog.wordpress.com/2010/01/16/fear-not-root/).

Sandfox does not aim to confine root - if someone has an exploit to get root access through your running Firefox as a normal user, your system is probably vulnerable whether Sandfox is running or not, although it would be a bit tougher for it if Sandfox is running.  But this is not the nature of most privacy issues introduced by Firefox and similar apps.  They don't rely on privilege escalation as much as basic access.  They run with your user privileges only, which gives them complete access to your data.

If privilege escalation was the primary issue in Firefox, you would see everyone's linux system not protected by AppArmor infected with viruses, Windows-style.  You don't see that because that kind of exploit is not common in Linux.  What is more common is the weekly vulnerability in Flash that allows 'arbitrary execution of code' - as a user, not root.  But as a user it has access to all the data you do as a user, as well as access to the Internet.  It does NOT have access to root-protected data - that is where Sandfox comes in.  Further, some plugins don't necessarily need to execute arbitrary code - they simply have access to the filesystem.

Sandfox is not 'app armor', it is more 'user data armor', and the way it builds that armor is by using core Linux commands as root in a fairly simple way.  That's why I refer to it as a poor man's sandbox - it just uses very basic tools to create a root-enforced sandbox.  The good news is those tools are core Linux commands that have been fairly well security-hardened.

What does that look like?  I am running Firefox right now in a sandbox.  If I try to save this page and the save as... dialog opens, many of my folders are simply not there.  It looks like someone has erased most of my filesystem, leaving just a few folders to run Firefox.  Java, Flash, and other child processes of Firefox see the same thing when they access the filesystem.  Many of the folders are just not there.  That is what Sandfox does.

Personally, I like this approach because it uses tools and commands I understand and which are part of the core Linux set, it doesn't drain system resources, it doesn't require any elaborate configuration or bloated libraries, and it's simple, which I think is good in security.  Understanding how security works makes for good security.  I don't like many convoluted security solutions because for all their complexity they often fail to address the most important things to a PC user.

At any rate, I'm not selling it - just explaining it as clearly as possible for those who have a use for such a thing.  You can also check out the 'How It Works' section on the website which has some further explanations of the details.

---

### Post by halfvulcan on 2010-02-08
Choice is a beautiful thing.  One can't make a valid argument against having more choices in a society that pretends to be free.  Thanks for giving us a very good choice, Ignorantguru.  It may not be as sophisticated and complex as the big ones, but it's easy to understand and it works for the purposes I needed a sandbox for.  I will view further criticism of it with extreme scrutiny.  Be specific about your criticism... because I'll be watching...  Muuuhahahahaaahaaaahaaaaa.

---

### Post by IgnorantGuru on 2010-02-08
lol  My pleasure!  Glad it's working well for you.

---

### Post by IgnorantGuru on 2010-02-09
_[Instructions have been added](http://igurublog.wordpress.com/downloads/script-sandfox/#startup)_ for starting Sandfox automatically at boot. This enables you to have a sandbox already open when the user logs in and starts programs, without the need to enter the root password.

Also, the default profiles have changed a bit in version 0.9.5. If you would like to see the new defaults, remove your /etc/sandfox folder and Sandfox will recreate the default profiles. If you are using an older firefox profile, it is suggested that you add “bind=/dev/urandom”, as Firefox uses this for security purposes.

---

### Post by halfvulcan on 2010-02-14
> **IgnorantGuru said:**
> If you are using an older firefox profile, it is suggested that you add &#8220;bind=/dev/urandom&#8221;, as Firefox uses this for security purposes.
Thanks.  I did, in fact, notice that when Firefox wouldn't start up and I traced it down using the methods in your readme.  Brilliant.  When something won't even start because I haven't allowed something it needs, I know it's being properly sandboxed.  Also, thanks for the daemon startup.  It's exactly what I needed, even though the daemon startup doesn't seem to be working, but it's likely something I'm doing wrong or forgetting.

---

### Post by IgnorantGuru on 2010-02-14
EDIT: Never mind all that about ps...  I thought you meant the user daemon, whereas you mean the init.d script.

---

### Post by IgnorantGuru on 2010-02-14
> **halfvulcan said:**
> Thanks.  I did, in fact, notice that when Firefox wouldn't start up and I traced it down using the methods in your readme.

Also, if your Firefox required something else to start, please let me know so I can consider including it in the default profile - thanks.

And I still want to see your Skype profile.  :)

---

### Post by DawieS on 2010-02-15
Thanks a lot! This is exactly what I needed.:grin:

I like the simplicity of the system. It is also very easy to customize. I have been playing around with it, and I like it a lot! I am sure Firefox runs faster as well.

I am using an updated recent fresh install of Ubuntu 9.10. For some reason I had to add the '.sh' suffix to the various 'sandbox' commands in your script, since I got the 'command not found' error message when I first tried to run as per your script.

Please correct me if I am wrong: If I run Firefox once outside the sandbox, setting up the site preferences, cookies etc. as per that last saved session, will all subsequent sessions have exactly that same 'profile' when run from within the sandbox? Thus all changes are discarded on exit? (Except of course downloaded files properly saved)?

This is great! Thanks again for your fantastic work!:grin:

---

### Post by IgnorantGuru on 2010-02-15
Hi - glad it's working well for you.

> **DawieS said:**
> I am using an updated recent fresh install of Ubuntu 9.10. For some reason I had to add the '.sh' suffix to the various 'sandbox' commands in your script, since I got the 'command not found' error message when I first tried to run as per your script.

When you download the script from the website it's named "sandfox.sh" (due to limitations of the webserver it can't be named "sandfox").  If you install it as "sandfox.sh", then you need to run it with that name.  Or you can rename it "sandfox".

> Please correct me if I am wrong: If I run Firefox once outside the sandbox, setting up the site preferences, cookies etc. as per that last saved session, will all subsequent sessions have exactly that same 'profile' when run from within the sandbox? Thus all changes are discarded on exit? (Except of course downloaded files properly saved)?

With the default Firefox sandbox profile, your ~/.mozilla folder is read-write accessible from within the sandbox.  So any changes you make in Firefox, such as settings, saved sessions, etc., are retained, and will appear the same when you run Firefox outside the sandbox.  Both Firefoxes access the same folder.

You can also set it up so changes made inside the sandbox are discarded.  In that case you could have sandfox create a disposable copy of your ~/.mozilla folder for the sandboxed Firefox to use, and it will be destroyed on exit.

Note that by default, the copy bind has a 50MB limit, although you can change this in the script to whatever you want (change the value of tmpfslimit in the pre-init section of the script).  I plan to raise this default to 100MB in the next update.  The copy bind uses tmpfs (RAM), so the 50MB limit is a safety limit to prevent a sandbox from consuming too much RAM.

Since ~/mozilla contains both Firefox settings and the cache, you may want to use two copy binds to give it 50MB + 50MB.  For example, add these to /etc/sandfox/firefox.profile...
```
copy=/home/$user/.mozilla
copy=/home/$user/.mozilla/firefox/XXXXXX/Cache
```
where "XXXXX" is your default profile folder in Firefox.  (You should also remove the bind=/home/$user/.mozilla from the profile).  Or, just raise the tmpfslimit in the script so one copy is large enough to hold your whole .mozilla folder.

Let me know if any of that isn't clear - there are also instructions on the blog on how to use copy.  Dealing with sandboxes can get fairly confusing so it's worth testing inside the sandbox to make sure it's behaving as you expect.  I've gotten myself mixed up a number of times!


Also, not related to what you wrote, I just want to announce that I made a change to the _[startup script instructions](http://igurublog.wordpress.com/downloads/script-sandfox/#startup)_.  One user reported it didn't work with Ubuntu, and I confirmed this.  It seems Ubuntu skips some runlevels, perhaps related to upstart.  At any rate, I revised the instructions so that links are added to every runlevel, and this appears to work, at least for me.

Thanks for your feedback.

---

### Post by DZ* on 2010-02-16
> **IgnorantGuru said:**
> Simply put, root may protect system files (the least valuable and most easily replaced data on your system)

I don't follow this. It's not data in system programs that's worth protecting, it's their behavior. If my OS makes it easy to covertly replace a remote login program with a custom version that lets someone in, then the fact that reinstall of that program is easy matters very little.

---

### Post by IgnorantGuru on 2010-02-16
> **DZ* said:**
> I don't follow this. It's not data in system programs that's worth protecting, it's their behavior. If my OS makes it easy to covertly replace a remote login program with a custom version that lets someone in, then the fact that reinstall of that program is easy matters very little.

Yes, those files do need protection, and root does that.  Least valuable does not mean non-valuable, it merely means less valuable than other data.  Why are you protecting the system files so no one can get in?  I would say to protect the more valuable data - which on a PC is the user's data, which is not generic or easily replaced.

That said, obviously if you don't protect system files (and thus system behavior), then you can't protect user files.  But protecting system files is not an end in itself, merely the first step.  Unfortunately most approaches to security in Linux go to great lengths to protect the system (behavior) but ignore the user's data as if it is unimportant.

Most apps don't need to be able to read or delete all user data, which is where sandboxes come in.  IMO this should be a fundamental part of the system rather than an add-on, but Linux itself doesn't give users that level of control.

---

### Post by DZ* on 2010-02-16
I'm thinking what you're doing is nice and I'm not against the idea of sandboxing applications.

What I'm saying is that I don't follow the argument where value of system data is contrasted with value of user data. Data in system files may have close to zero value, yet there needs to be assurance of their integrity for the reasons that have nothing to do with their replaceability. 

I don't compare the value of my car with the value of my life when I go to replace faulty brakes. If I did, I'd say hell with the brakes, let the car wreck -- I'll just get a new one.

I doubt that "many devs are thinking that the most valuable data are the system files". It's not data in system files that need protection. It's the advertised behavior of programs that needs to remain as advertised.

---

### Post by halfvulcan on 2010-02-20
For a simple and short explanation of the benefits of a sandbox, I recommend going to sandboxie.com.  Right there on his front page. "Trust no program".  Some of us find ourselves in a situation of having to use certain communications software because friends and family use it.  We don't have the source code for it, but we use it because we have to.  Well, that doesn't mean we have to trust it.  Block that sucka.  Don't let it see or modify more than it needs to do the only thing it's SUPPOSED to be doing.
Also, Firefox may be somewhat trustworthy until you install extensions and plugins.  And I don't know about you, but one reason I'm still using Firefox is because of the capabilities and customizability added by extensions, but I sure don't trust them and I don't know how to inspect the code they consist of.  This gives me a way of saying "you shall not pass!"

---

### Post by halfvulcan on 2010-02-20
> **IgnorantGuru said:**
> If you are using an older firefox profile, it is suggested that you add “bind=/dev/urandom”, as Firefox uses this for security purposes.
I think I also had to give it access to /dev/random.

---

### Post by IgnorantGuru on 2010-02-20
Sandfox has been updated to 0.9.6.  Three changes:  Sandfox can now bind /dev/random, which may be necessary for printing in Firefox (my Firefox 3.6 crashes if I select File|Print without it).  It is suggested that you add "bind=/dev/random" to your Firefox profile, or delete your profile and Sandfox will recreate it with the new default.

Also, the copy and hide tmpfs size has been raised to 100MB.  You can also adjust this yourself by editing the line "tmpfslimit=100M" in the script.

And a user-contributed Skype profile has been added - feedback welcome.

[http://igurublog.wordpress.com/downloads/script-sandfox/](http://igurublog.wordpress.com/downloads/script-sandfox/)

---

### Post by IgnorantGuru on 2010-02-20
> **halfvulcan said:**
> I think I also had to give it access to /dev/random.

On Arch at least, this used to cause mount to hang.  But I have corrected this in 0.9.6.

---

### Post by DZ* on 2010-02-20
> **halfvulcan said:**
> Some of us find ourselves in a situation of having to use certain communications software because friends and family use it.  We don't have the source code for it, but we use it because we have to.  Well, that doesn't mean we have to trust it. 

Could you share instructions on how you sandbox that certain application?

---

### Post by halfvulcan on 2010-02-21
The instructions for sandfox on IgnorantGuru's blog page provide a method for creating profiles for applications.  There's usually trial and error and some testing involved.  I tend to start by looking on the internet for an apparmor profile for whatever application I'm trying to barricade.  I'm certainly not a pro with this yet though.

---

### Post by bodhi.zazen on 2010-02-21
> **halfvulcan said:**
> The instructions for sandfox on IgnorantGuru's blog page provide a method for creating profiles for applications.  There's usually trial and error and some testing involved.  I tend to start by looking on the internet for an apparmor profile for whatever application I'm trying to barricade.  I'm certainly not a pro with this yet though.

+1

IgnorantGuru's Sandbox has rather uniques goals and is extremely limited compared to either selinux or apparmor.

No offense intended, but IgnorantGuru has a healthy mistrust of both selinux and apparmor.

So while this sandbox may work for IgnorantGuru, for anyone else, be sure you understand the limitations and alternates, in particular Apparmor or Selinux, before you dive into this technique.

Again, no offense to IgnorantGuru's, it is a nice technique and s/he spent a ton of time on this, but we are talking security here and I am simply stating what should be obvious, do not blindly follow this technique without evaluating it fully, including the advantages and disadvantage as well as the alternatives.

As I have stated earlier, I trust the integrity of my system to Apparmor and this sandbox, IMO, would be relatively easy to break out of if there is a security flaw with the underlying application.

This technique may isolate a user form his or her self, but offers very little, if any, protection of system files and similar results can be obtained, IMO, either using the guest account or creating a limited account for daily use.

Again, no offense to IgnorantGuru or anyone who finds this technique helpful, just understand the limitations before you follow it.

---

### Post by IgnorantGuru on 2010-04-22
Sandfox  has reached version 1.0.0, meaning it has proved itself stable. Actually after running it for months I’ve had great results with it. The only change in this version is that /dev/urandom is now treated like /dev/random – both are not remounted to prevent mount hanging on some systems (one user reported having a problem with a /dev/urandom mount hanging).

As far as a security record at this point, Sandfox has been downloaded many hundreds of times - it has become the second most popular download on the site, and has been discussed here, on the Arch Linux forums, and elsewhere.  Thus far no one has demonstrated any exploits nor raised any substantiated security problem.

[http://igurublog.wordpress.com/downloads/script-sandfox/](http://igurublog.wordpress.com/downloads/script-sandfox/)

---

### Post by arapaho on 2011-03-17
Please, vote \\:D/
[[IMG]http://brainstorm.ubuntu.com/idea/27401/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/27401/)

---

### Post by IgnorantGuru on 2011-03-17
I also voted for your other idea re the firewall - that is sorely needed in Linux and has been for awhile.

In the easy to use department, sandfox does make it as simple as "sandfox firefox" or "sandfox skype", although there aren't any provided profiles for the other programs you mentioned.

---

### Post by arapaho on 2011-03-17
Thank you. And thank you for sharing your work.
Actually idea #26902: ref. firewall is not my idea but I voted for it too.
I hope idea of sandboxing applications becomes popular. I'd be happy if there was a kind of GUI application control center allowing to control security issues in Ubuntu, including sandboxing. Actually there are 'ideas' about it
Idea #1282: Security and stability centre
[http://brainstorm.ubuntu.com/idea/1282/](http://brainstorm.ubuntu.com/idea/1282/)
Idea #19648: Security Center
[http://brainstorm.ubuntu.com/idea/19648/](http://brainstorm.ubuntu.com/idea/19648/)
and discussion:
[https://lists.ubuntu.com/archives/ubuntu-hardened/2010-April/subject.html](https://lists.ubuntu.com/archives/ubuntu-hardened/2010-April/subject.html)

But I'm a total newbie and I can only vote. I hope developers take into account public requests. ):P

---

### Post by bodhi.zazen on 2011-03-17
FYI: As I mentioned earlier ...

1. Apparmor provides most of not all of this functionality in Ubuntu.

IMHO I think you would be much better off learning apparmor and/or writing refining the various apparmor profiles.

2. Fedora has been working of a sandbox confined by selinux since Fedora 12.

Here is but one example:

[http://www.bress.net/blog/archives/195-Firefox-in-a-sandbox-with-Fedora.html](http://www.bress.net/blog/archives/195-Firefox-in-a-sandbox-with-Fedora.html)

So again I think it is best to join / contribute to existing projects and personally I would trust apparmor, selinux, openvz, LXC, pax/grsecurity far more then this project.

If you wish to use Ubuntu, much of what you are wanting already exists with apparmor.

---

### Post by archolman on 2011-03-17
I like this Sandfox idea. I'm not a newby, but I'm not that conversant with configuration-file handling/editing, permissions, etc. This is what Apparmor & SELinux aren't, that is, easy to use.

 Simple and comparatively robust security is the answer to most users questions in this area. I think Sandfox gives me a tool that is within my competence of using bash.

Having said that, if Apparmor & SELinux came with a comprehensive GUI, I would be using one of those. Point & click has to be the way to enable general users to feel confident when dealing with security.

Apparmor is probably the best GNU/Linux SOHO solution, but when, say, your're running a small business, who's got the time to mess with it, especially when your not sure of what's needed. SELinux or Bastille seem even more complicated. They are techhead solutions, not general users tools. The Sandfox idea is closer to the general users competence than the alternatives.

---

### Post by bodhi.zazen on 2011-03-18
> **archolman said:**
> Having said that, if Apparmor & SELinux came with a comprehensive GUI, I would be using one of those.

You obviously have not tried Fedora 14 as it comes with selinux enabled and as comprehensive a gui as you would want.

The gui tools notify you of alerts and as a part of the alert they (usually) include the necessary steps to resolve the problem. Sometimes at the click of a button, sometimes running a command.

On my F14 desktop I have not had to do anything with selinux configuration, it works out of the box.

You will get alerts if you do something unexpected (such as install an application form source code or run a service on a non-standard port), but the graphical tools will walk you through the fix most of the time.

In addition to the alerts, there are graphical tools to modify the selinux policies, if you feel you need to. Typically this would be setting a Boolean allowing you to serve a file or directory samba or nfs share through apache. Something like that would be unusual but you can make the necessary modifications via the graphical interface.

The advantage of Fedora 14 is that 
1. There are working policies out of the box.
2. The policies are quite mature and most users do not nee dto modify them.
3. When there is a problem you can almost always manage them from the graphical tools.

For Apparmor, on Ubuntu, simply install the apparmor profiles:

```
sudo apt-get install apparmor-profiles
```

There is already a profile for firefox and it works for most people without further intervention.

Unfortunately there are insufficient graphical tools to manage apparmor in Ubuntu.

The advantage of apparmor is that it is faster to learn.

The disadvantages are that:
1. The profiles are less mature then selinux (or lacking) meaning users need to spend time modifying or writing policies.
2. There is a lack of graphical tools to manage apparmor.

---

### Post by IgnorantGuru on 2011-03-18
Re AppArmor and SELinux, I would just add a few cautionary notes.

In my limited experience with default profiles in such security solutions, they are often very loose, which is why they work so well.  They are often more geared toward protecting the system and system files than they are your personal files or info.  For example, a default Firefox profile will probably give Firefox (and thus any Firefox exploits) access to all your user-accessible files.  (If it didn't, you wouldn't be able to save files to your home folder from within Firefox, for example.)  Nothing wrong with starting with a default profile, but depending on what your goal is, you may want to tighten down aspects of it.  ([Fear Not Root](http://igurublog.wordpress.com/2010/01/16/fear-not-root/) is a good read on this subject.)

Second, as I believe was discussed earlier in this thread, these robust security solutions are often created with the (overt and covert) involvement of government agencies who specialize in spying, and are influenced by corporations that don't necessarily have YOUR security in mind.  Put simply, they very likely contain backdoors of various sorts.  This is common in the Windows world, where anti-virus software often has other things going on as well.  Thus, some people don't trust these types of security solutions, either because they don't trust these entities, or they feel any backdoors could be used by others.  In addition, they are very complex, with many thousands of lines of code - many places to hide exploits (even open-source code is not peer-reviewed nearly as much as is commonly claimed, and exploits are rarely discovered this way).

Sandfox is not in their category - a filesystem sandbox, it cannot provide the network and other robust system protections that they provide.  But it is simple and transparent, uses only basic Linux tools to construct the sandboxes, and uses virtually no resources.  You might consider it more of a security enhancement, but a fairly strong one in terms of filesystem access (generally as strong as the filesystem protections in Linux).  

Use whichever fits you best - I just wanted to clarify the differences.

---

### Post by bodhi.zazen on 2011-03-18
> **IgnorantGuru said:**
> Re AppArmor and SELinux, I would just add a few cautionary notes.

In my limited experience with default profiles in such security solutions, they are often very loose, which is why they work so well.  They are often more geared toward protecting the system and system files than they are your personal files or info.  For example, a default Firefox profile will probably give Firefox (and thus any Firefox exploits) access to all your user-accessible files.  (If it didn't, you wouldn't be able to save files to your home folder from within Firefox, for example.)  Nothing wrong with starting with a default profile, but depending on what your goal is, you may want to tighten down aspects of it.  ([Fear Not Root](http://igurublog.wordpress.com/2010/01/16/fear-not-root/) is a good read on this subject.)

Yes and no. Because of #2 you are not really familiar with selinux or apparmor so you do not really know how they work or what the options or limitations are.

I agree with your point that in addition to system files , files in /home need to be locked down.

For example, there is (typically) no reason firefox needs access to ~/.ssh (and other files).

Apparmor and selinux both have the ability to lock down files in /home, yes you need to configure them properly, especially apparmor, but doing so is trivial, and there is an include for apparmor for "private files".

The biggest flaw in your method is that system files are not in any way protected.

> Second, as I believe was discussed earlier in this thread, these robust security solutions are often created with the (overt and covert) involvement of government agencies who specialize in spying, and are influenced by corporations that don't necessarily have YOUR security in mind.  Put simply, they very likely contain backdoors of various sorts.  This is common in the Windows world, where anti-virus software often has other things going on as well.  Thus, some people don't trust these types of security solutions, either because they don't trust these entities, or they feel any backdoors could be used by others.  In addition, they are very complex, with many thousands of lines of code - many places to hide exploits (even open-source code is not peer-reviewed nearly as much as is commonly claimed, and exploits are rarely discovered this way).

Without a citation this is a hypothesis, conspiracy theory, or paranoia at best. I assume you obtained bash from canonical as you are posting on the Ubuntu Forums. Canonical is a corporation last time I looked ;)

Unless you are using LFS and unless you reviewed your compiler and the source code yourself you are vulnerable to these threats and your script does not change that fact.

A back door, and it only takes one ;) , such as you hypothesize, could be anywhere in your system files from the kernel itself to netfilter. Why would the various entities you fear target selinux or apparmor ? Those are both security applications and the paranoid penguins are going to review that code more then most. A back door in these apps would stand out like a sore thumb.

Far better to target the kernel or netfileter.

Now since your sandbox does not guard against system files, it does nothing to protect against the backdoors you fear. You simply can not ignore the integrity of the kernel and expect a bash script to provide any type of safety net.

> Sandfox is not in their category - a filesystem sandbox, it cannot provide the network and other robust system protections that they provide.  But it is simple and transparent, uses only basic Linux tools to construct the sandboxes, and uses virtually no resources.  You might consider it more of a security enhancement, but a fairly strong one in terms of filesystem access (generally as strong as the filesystem protections in Linux).  

Use whichever fits you best - I just wanted to clarify the differences.

No sandfox is nowhere close to a selinux sandbox.

You can obtain similar results with Virtualbox, a live CD, LXC, a chroot, apparmor, etc, etc. Any of those options at least offers some semblance of isolation.

If you do not trust selinux or apparmor, find an alternate solution you do trust (pax / grsecurity, other ?)

---

### Post by archolman on 2011-03-20
> **bodhi.zazen said:**
> You obviously have not tried Fedora 14 as it comes with selinux enabled and as comprehensive a gui as you would want.

  Thanks Bodhi, I may well leave the Ubuntu fold for Fedora :), especially as Ubuntu seems set to drop the Gnome desktop. 

@IgnorantGuru: Good luck with the Sandfox project.

---

### Post by cariboo on 2011-03-20
<offtopic>
I just installed Fedora 15, gnome-shell is the default desktop.
</offtopic>

---

