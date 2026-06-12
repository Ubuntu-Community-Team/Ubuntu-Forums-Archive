---
title: "Dohickey 0.7 Release - Intergration and Maturity"
date: 2008-02-11
forum: The Cafe
---

### Post by DoctorMO on 2008-02-11
Hello Ubuntu folks,

OK I've finally decided to release 0.7, I should have done this a long
time ago and broke the "release early, release often" philosophy but here it is! a new release:

Download: [www.dohickey-project.com/client/download.shtml](www.dohickey-project.com/client/download.shtml)
ChangeLog: [https://sourceforge.net/project/shownotes.php?release_id=575534](https://sourceforge.net/project/shownotes.php?release_id=575534)

This release comes with a couple of exciting elements, the cpu and ram
items add extra bulk to the hardware view. The view modes allow for
you to specify what ever mode you feel most comfortable working in.
And the drivers section will now tell you what kind of drivers are
being used by that device.

The website integration has been going well too, we're working on
standardising all the packages for the server side so it can be
installed very easily in future. But we have a working demo server at
[http://dohickey.parsed.net/](http://dohickey.parsed.net/) The one at dohickey-project.com will not
be able to be updated as dream host doesn't allow us to install Lucene
text indexing for the search features. The server side now boasts some
nice browsing and searching screens and you can submit your hardware
data as a test of the client to this site also, just configure it in
the option menu.

To come in the future (we hope) is to send the driver information to
the server in a meaningful way, we hope to create a link between
hardware as identified and the drivers they use; We're then going to
link that to the development of those drivers and then on to have a
button which reports problems with a particular piece of hardware. The
end goal is to have the kernel, cups, sane (whoever) guys aware of end
user problems by removing the glut of barriers that people have in
communicating in the same language and being able to report the
correct metrics. We'd also like to work with Canonical and Dell to
develop a system of reporting failures in hardware systems to ease
support.

Big thanks go to Aaron (guinea-pig), Mindfulgeek and ubuntu-ma and my
wife for putting up with my obsession. :-D

All bugs should be reported here:
[https://sourceforge.net/tracker/?group_id=177020&atid=879565](https://sourceforge.net/tracker/?group_id=177020&atid=879565) or
emailed to me personally [email]doctormo@gmail.com[/email] or just post here, I'll subscribe to the post.

Wiki Docs: [http://dohickey.wikispaces.com/](http://dohickey.wikispaces.com/)

Thanks all.

---

### Post by DoctorMO on 2008-02-11
I'd also like to point out that Aaron wants the demo site to be used just for testing. As bandwidth can get pricey if 3 million people start doing things.

---

### Post by leftorvo on 2008-02-11
Looks interesting, hardware always seems to be an issue to someone.

---

### Post by DoctorMO on 2008-02-11
It does, especially the problem of buying hardware which is something we want to solve.

---

### Post by leftorvo on 2008-02-11
Yeah, i'd hate to use linux for years and then buy a new piece of hardware and have it not work.

---

### Post by DoctorMO on 2008-02-11
Well it's also to give new users confidence that they can find what they want.

We're also hoping that if enough people use the same resource that our ratings will put pressure on manufacturers since we'll be advising people against buying their product because of lack of linux support.

---

### Post by DoctorMO on 2008-02-11
We've added an apt repository so all our lovely testers and helpers can keep their dohickey up to date without doing anything!

[http://dohickey-project.com/client/download.shtml](http://dohickey-project.com/client/download.shtml)

Please test if you can, it helps a huge deal.

---

### Post by PGTips91 on 2008-02-12
I have tried installing dohickey_0.7_all.deb in Klikit-Linux 0.1-8 [based on Kubuntu 7.04]
and get an error message and the installation does not succeed : -- 

Error: Dependency is not satisfiable: libhal1

although Synaptic says that the required application is installed : --

libhal1-0.5.8.1-4ubuntu12 (feisty)

What do I need to do to get this later version installed?

---

### Post by DoctorMO on 2008-02-12
libhal1 should be enough, we're looking into it; on kde the gtk libs would be needed too.

---

### Post by DoctorMO on 2008-02-12
OK the problem has been fixed, you can try again; I recommend using the apt-get method mentioned above.

---

### Post by PGTips91 on 2008-02-14
> **DoctorMO said:**
> OK the problem has been fixed, you can try again; I recommend using the apt-get method mentioned above.

Hi,

I tried the apt-get method but got errors trying to add the new repository and failed.

While I was wondering how I could find out more, I did an update using the Klikit update notifier and found that the latest version of Dohickey 0.7 was already included. It would be from the Kubuntu repositories I think. Any way, I now have the latest version installed and will give it another whirl in a little while, when I have the time.

Thanks for the support here.

Paul

PS Report submitted.
      Help > About still reports Dohickey 0.6.1

---

### Post by FuturePilot on 2008-02-14
Is Help&#8594;Dohickey Help supposed to launch a root Firefox?

---

### Post by PGTips91 on 2008-02-14
> **FuturePilot said:**
> Is Help&#8594;Dohickey Help supposed to launch a root Firefox?


I just tried it, and it created a new instance of Firefox rather than just adding a 'tab' to the existing instance of Firefox.

The Wiki web site does not yet reflect the latest release, finishing at v 0.6.1, the previous release, instead.

---

### Post by macogw on 2008-02-14
You can't sudo echo .... > /etc/apt/sources.list  You'll get a permission denied before it even asks for your password.  This works though:
```
sudo sed -i '$a\\n\# Dohickey repo\ndeb http:\/\/ubuntu.parsed.net gutsy\/dohickey main' /etc/apt/sources.list
```

Also, what keyserver is the GPG key on?

---

### Post by DoctorMO on 2008-02-14
> Is Help&#8594;Dohickey Help supposed to launch a root Firefox?

Good point, I better ponder how to fix that. [https://bugs.launchpad.net/dohickey/+bug/191768](https://bugs.launchpad.net/dohickey/+bug/191768)

> Also, what keyserver is the GPG key on?

I'm not sure since it's managed by aaron; i'll pass the question on.

> You can't sudo echo .... >

Thanks, I'll fix it right up.

---

### Post by PGTips91 on 2008-02-14
> **DoctorMO said:**
> 

I'm not sure since it's managed by aaron; i'll pass the question on.



When I remembered to do the requisite reboot after my updates I received an error messages saying that it could not find the GPG key for Dohickey. 

The 0.7. version is reported as installed, in Synaptic, though.

However, when I opened Dohickey and click on > Help > About it still shows version 0.6.1.

---

### Post by DoctorMO on 2008-02-14
Ah I see, I've updated it; to be honest i centralised every version variable apart from that one so I forgot about it. thanks for letting me know.

---

### Post by PGTips91 on 2008-02-14
> **DoctorMO said:**
> Ah I see, I've updated it; to be honest i centralised every version variable apart from that one so I forgot about it. thanks for letting me know.

You're welcome.

BTW, Synaptic now reports that it has updated from 0.6.2 to 0.7. but the "About" still said 0.6.1, so the problem was there earlier. Not so important, but, for me, trying to trace what is happening on my system, it will help to have the right values displaying.

Will this percolate through automatically to the repository that I am drawing from?

As you can see, I am running Klikit-Linux and we are expecting a new version release any day now. Once the excitement of that has passed a little, I will try and push this project there. How well is the database side working?

Paul

---

### Post by DoctorMO on 2008-02-14
> Will this percolate through automatically to the repository that I am drawing from?

I'll get a new version released when I have more fixes.

> As you can see, I am running Klikit-Linux and we are expecting a new version release any day now. Once the excitement of that has passed a little, I will try and push this project there. How well is the database side working?

It's getting better, the submission process is working and the administration works. It's the testing and peer review that's suffering really.

---

### Post by PGTips91 on 2008-02-14
> **DoctorMO said:**
> I'll get a new version released when I have more fixes.

Great, I'll just wait for it to update itself.

> 
It's getting better, the submission process is working and the administration works. It's the testing and peer review that's suffering really.

You mean that you would like more users?

Klikit forum is quite small but it has some that are fairly up on their hardware. I'll wait a bit and see if I can get some interest in this project over there. I see this as a great tool for collecting information on what works and what doesn't work with a distribution. Can the database be filtered on the OS?

Paul

---

### Post by DoctorMO on 2008-02-14
> Can the database be filtered on the OS?

For the reviews/ratings yes, but the gearing isn't set up for anything other than linux at the moment.

---

### Post by notwen on 2008-02-14
Wow, glad to see this project has progressed a lot from when I stumbled across it months ago her eon the forums.  I'll be sure to try it out. =]

---

### Post by DoctorMO on 2008-02-14
I'm working on it as much as I can, it being in my spare time. Any help would be _very_ useful.

---

### Post by PGTips91 on 2008-02-14
> **DoctorMO said:**
> I'll get a new version released when I have more fixes.

It's getting better, the submission process is working and the administration works. It's the testing and peer review that's suffering really.

Just one more minor error to report. I have just updated Synaptic and got this error message : --

> W: GPG error: [http://ubuntu.parsed.net](http://ubuntu.parsed.net) gutsy/dohickey Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2F290C15E802C30

I'm running Klikit-Linux, based on Feisty, so I don't quite understand the reference to Gutsy. This is just for your information.

Paul

---

### Post by pt123 on 2008-02-14
Great Idea but useless if the results aren't published. 

Is there anyway to browse the best rated motherboards, mouses, etc.

---

### Post by DoctorMO on 2008-02-14
> Great Idea but useless if the results aren't published.

Is there anyway to browse the best rated motherboards, mouses, etc.

Well yes, [http://dohickey.parsed.net/](http://dohickey.parsed.net/) is the test server, I'm going to change the links from the main site so it's not confusing any more.

---

### Post by DoctorMO on 2008-02-14
> W: GPG error: [http://ubuntu.parsed.net](http://ubuntu.parsed.net) gutsy/dohickey Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2F290C15E802C30

My server admin tells me that this is because you failed to apply the key right.

---

### Post by PGTips91 on 2008-02-14
> **DoctorMO said:**
> Well yes, [http://dohickey.parsed.net/](http://dohickey.parsed.net/) is the test server, I'm going to change the links from the main site so it's not confusing any more.

I've had a look and there is not much there yet. The concept is working, but where are the comments, ratings, 'best supported' hardware, etc?

Is there a plan for further development?

---

### Post by PGTips91 on 2008-02-14
> **DoctorMO said:**
> My server admin tells me that this is because you failed to apply the key right.

Hi,

I'm out of my depth here. 

When I tried to do the update manually, from a Konsole window, I got error messages, which were relating to the PGP if I remember correctly,  and could not proceed. 

Later, I was able to update via Synaptic to the latest version but am still getting this error message on the first reboot.

It seems to me that it is no longer something that I should be doing since the update came through a normal automatic procedure. But I am open to any advice - just be quite detailed please.

---

### Post by DoctorMO on 2008-02-14
> I've had a look and there is not much there yet. The concept is working, but where are the comments, ratings, 'best supported' hardware, etc?

Where is the help? the admins? and the _people_ that are needed to run such things? I am but one programmer trying to give the community to the tools to do the job. If the community doesn't choose to use those tools to fill in such information then there is very little i can do.

the only way to get information into that data base is to enter it yourself, and getting your friends to enter it etc.

Development will continue until at least version 1.0 is released if not forever.

> When I tried to do the update manually, from a Konsole window, I got error messages, which were relating to the PGP if I remember correctly, and could not proceed.

Did you do these steps:

```
sudo gpg --recv-keys 5E802C30
sudo gpg --export 5E802C30 | sudo apt-key add -
```

Doing these steps again may solve your key problem.

---

### Post by PGTips91 on 2008-02-14
> **DoctorMO said:**
> Where is the help? the admins? and the _people_ that are needed to run such things? I am but one programmer trying to give the community to the tools to do the job. If the community doesn't choose to use those tools to fill in such information then there is very little i can do.

the only way to get information into that data base is to enter it yourself, and getting your friends to enter it etc.

Development will continue until at least version 1.0 is released if not forever.


I hear you. I'm not complaining, just trying to find out the state of the game here. I will try and garner you some support if I can. I'm not much use on my own, unfortunately.

> 
Did you do these steps:

```
sudo gpg --recv-keys 5E802C30
sudo gpg --export 5E802C30 | sudo apt-key add -
```

Doing these steps again may solve your key problem.

> paul@PAULS-Klikit:~$ sudo gpg --recv-keys 5E802C30
gpg: directory `/home/paul/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/paul/.gnupg/secring.gpg' created
gpg: keyring `/home/paul/.gnupg/pubring.gpg' created
gpg: no keyserver known (use option --keyserver)
gpg: keyserver receive failed: bad URI
paul@PAULS-Klikit:~$ sudo gpg --export 5E802C30 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
paul@PAULS-Klikit:~$


---

### Post by DoctorMO on 2008-02-15
OK the problem was with the instructions (now corrected)
```

gpg --keyserver subkeys.pgp.net --recv-keys 5E802C30
sudo gpg --export 5E802C30 | sudo apt-key add -
```

These are the right ones.

---

### Post by PGTips91 on 2008-02-15
> **DoctorMO said:**
> OK the problem was with the instructions (now corrected)
```

gpg --keyserver subkeys.pgp.net --recv-keys 5E802C30
sudo gpg --export 5E802C30 | sudo apt-key add -
```

These are the right ones.

Well after two failed attempts, I have now succeeded in importing the key. After some time I pinged the server and got a response, so I had another go which did get a response.

> paul@PAULS-Klikit:~$ sudo gpg --keyserver subkeys.pgp.net --recv-keys 5E802C30
gpg: requesting key 5E802C30 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
paul@PAULS-Klikit:~$ ping subkeys.pgp.net
PING subkeys.pgp.net (213.239.206.174) 56(84) bytes of data.
64 bytes from subkeys.pgp.net (213.239.206.174): icmp_seq=1 ttl=53 time=331 ms
64 bytes from subkeys.pgp.net (213.239.206.174): icmp_seq=2 ttl=53 time=334 ms
64 bytes from subkeys.pgp.net (213.239.206.174): icmp_seq=3 ttl=53 time=332 ms
64 bytes from subkeys.pgp.net (213.239.206.174): icmp_seq=4 ttl=53 time=332 ms
64 bytes from subkeys.pgp.net (213.239.206.174): icmp_seq=5 ttl=53 time=336 ms
64 bytes from subkeys.pgp.net (213.239.206.174): icmp_seq=6 ttl=53 time=331 ms

--- subkeys.pgp.net ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5011ms
rtt min/avg/max/mdev = 331.366/333.245/336.609/1.765 ms
paul@PAULS-Klikit:~$ sudo gpg --keyserver subkeys.pgp.net --recv-keys 5E802C30
gpg: requesting key 5E802C30 from hkp server subkeys.pgp.net
gpg: /home/paul/.gnupg/trustdb.gpg: trustdb created
gpg: key 5E802C30: public key "Parsed.Net Package Signing Key <admin@parsed.net>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
paul@PAULS-Klikit:~$ sudo gpg --export 5E802C30 | sudo apt-key add -
OK
paul@PAULS-Klikit:~$


I reloaded Synaptic, this time without any errors reported. Looks like it's good to go.

Thanks for your support.

Paul

---

### Post by aaaantoine on 2008-02-15
Got this with apt-get update:
```
Failed to fetch http://ubuntu.parsed.net/dists/gutsy/dohickey/Release  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
```

Is there a 64-bit deb?

---

### Post by DoctorMO on 2008-02-15
It's python based so technically there is no 64bit version because there is no 32bit version. it's just all one version. I'm talking to the repository maintainer to see if anything can be done for 64bit people.

---

### Post by macogw on 2008-02-15
> **DoctorMO said:**
> It's python based so technically there is no 64bit version because there is no 32bit version. it's just all one version. I'm talking to the repository maintainer to see if anything can be done for 64bit people.

In the debian control files, you should be able to specify "all" for the architecture.  Oh wait...looking at the tar, you did.  That's confusing...

```
The following NEW packages will be automatically installed:
  libgtkhtml2-0 libgtksourceview-common libgtksourceview1.0-0 libmetacity0
  libpanel-applet2-0 libwnck-common libwnck22 libxres1 metacity-common
  python-dbus python-gnome2-desktop python-gtkhtml2
```
Some of those I don't see anything odd about because I don't know what they do, exactly (I assume anything libgtk* is just for widgets, so whatever), but why libpanel-applet2-0, libmetacity0, and metacity-common?  Previous versions of Dohickey weren't panel applets.  Has something changed?  Will not using/having a panel (I'm using Fluxbox) make a difference to how Dohickey works?

Oh, clicking on either the "Source tar archive" link or the "Ubuntu / Debian installer" link on the download page takes you to [https://sourceforge.net/project/showfiles.php](https://sourceforge.net/project/showfiles.php) which is just an error page.  It should go to [http://sourceforge.net/project/showfiles.php?group_id=177020](http://sourceforge.net/project/showfiles.php?group_id=177020)

---

### Post by DoctorMO on 2008-02-15
> Some of those I don't see anything odd about because I don't know what they do, exactly (I assume anything libgtk* is just for widgets, so whatever), but why libpanel-applet2-0, libmetacity0, and metacity-common? Previous versions of Dohickey weren't panel applets. Has something changed? Will not using/having a panel (I'm using Fluxbox) make a difference to how Dohickey works?

the libpanel dependencies are unknown to me. It sounds like they've been added by aaron who had a poke around to find all the deps and they might not be required now.

And the links should be fixed now.

---

### Post by macogw on 2008-02-15
There should be an icon key on the website, I think.  I couldn't figure out what the difference was between:
[img]http://dohickey.parsed.net/images/hardware/bus/pci.png[/img]
and
[img]http://dohickey.parsed.net/images/hardware/bus/pcie.png[/img]
on the wireless cards until I saw what the URLs were for each image.

---

### Post by DoctorMO on 2008-02-15
> There should be an icon key on the website, I think. I couldn't figure out what the difference was between:

I could easily do it, but I have no idea where in the website it make sense to add such a key. :-/

---

### Post by pt123 on 2008-02-15
> **DoctorMO said:**
> Well yes, [http://dohickey.parsed.net/](http://dohickey.parsed.net/) is the test server, I'm going to change the links from the main site so it's not confusing any more.

I browsed some of the hardware and was not able to get any of the ratings on them? Is it possible to have a top rated section.

---

### Post by DoctorMO on 2008-02-15
> I browsed some of the hardware and was not able to get any of the ratings on them? Is it possible to have a top rated section.

Sure but with only 2 items in that database having ratings it makes it a little irrelivent. I'll make a note to add a rating value to the listing and browsing.

Oh and please do create bug reports in launchpad, we're up there as a project and your problems are more likely to be worked on if there is a list somewhere I can come back to.

---

### Post by pt123 on 2008-02-15
> **DoctorMO said:**
> 
Oh and please do create bug reports in launchpad, we're up there as a project .
OK, I have had bad experiences with Launchpad & Ubuntu, many people will report a bug then the developer (Nautilus)  will come and assign it a low priority without giving a single explanation. 

Maybe smaller applications will be more informative.

---

### Post by DoctorMO on 2008-02-15
> Maybe smaller applications will be more informative.

If there are any problems with a bug you know who to complain to, me. [email]doctormo@gmail.com[/email] is email address. Just so long as you know I have limited time in the hours of the day and it may be worth providing as much information and trying to help out where you can.

---

### Post by macogw on 2008-03-06
The directions for apt on the download page were switched back to using echo and a redirect...that'd still require already being in a root shell.  Sudo can't do it.  The sed thing I gave earlier works.

---

### Post by DoctorMO on 2008-03-06
Sorry about the confusion, there was a merging of websites between dohickey-project.com and dohickey.parsed.net which caused some conflicts; this was one of them.

guinea-pig committed the change, I shall have to ask him about it incase there was a special reason.

---

### Post by user1397 on 2008-03-26
Wow DoctorMO, dohickey is lookin' mighty fine!

Thanks for all your hard work, and of others who have contributed into this project. :)

---

### Post by DoctorMO on 2008-03-26
Thanks for your kind words, much work is ahead to get it to a very useful state.

---

