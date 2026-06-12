---
title: "Questions about submitting a closed-source app"
date: 2013-01-17
forum: Ubuntu Application Development
---

### Post by stqn on 2013-01-17
Hi,

I want to submit a closed-source (proprietary) application for inclusion in the software center, but couldn’t find a lot of information on the topic. I would be grateful for information on the following:

- I read somewhere that the app should be built for the latest version of Ubuntu, which would be 12.10 at the moment. But I want my app to work under 12.04 LTS too. Should I provide 2 binaries? In that case, should I include a launcher script to select the correct binary automatically?

- Should I provide both x86 and x86-64 binaries?

- My app uses SDL, SDL image and SDL mixer. Should I include them in the archive (so that the app continues working in future versions of Ubuntu), or are we relying on me/the user updating the app for each new release of Ubuntu?

- Will users have to update manually from the software center when I release updates? (In which case I should probably inform them of available updates in-app.)

Thanks!

---

### Post by Retro Banana on 2013-01-18
1. You will most likely need to build a .deb for each release of Ubuntu you plan on supporting...
2. ...and each architecture. Technically x86 code will work on x86_64 CPUs, it might not runas well as x86_64 code.
3. Make all three dependencies of the package.
4. No, the update manager will take care of that for you.

---

### Post by deadflowr on 2013-01-18
You'll first have to release the software in a ppa before the Ubuntu developers decide to include it in any repositories.
Look at this on how:

[https://launchpad.net/+tour/ppa]("https://launchpad.net/+tour/ppa") 

Most likely if you are going to keep it closed, then you'll want to subscribe for a private ppa.

---

### Post by stqn on 2013-01-28
Thank you for your answers. I spent several hours browsing askubuntu and elsewhere and came up with&#8230;

- a private PPA costs 250$ per year so that&#8217;s not an option at this point. Although one Canonical employee seem to have proposed to turn a public PPA to a private one especially for the purpose of releasing a proprietary app to the USC, but I don&#8217;t know if they finally did it ( [http://askubuntu.com/a/170015](http://askubuntu.com/a/170015) ).

- I could upload a source package ( [http://askubuntu.com/a/100165](http://askubuntu.com/a/100165) ) which would solve all the 32/64 bit and ubuntu versions problems, since Canonical could build all versions themselves, but at the moment I&#8217;d prefer to keep my source to myself.

- Retro Banana is right on all points, but proprietary apps can also simply be submitted in a .tar.gz. I can include several binaries inside it and give the packager some documentation about the architectures/ubuntu releases/dependencies needed ( [http://askubuntu.com/a/85146](http://askubuntu.com/a/85146) ).

I&#8217;ll most likely submit only 32 bit versions, for 12.04 LTS and 12.10.

Additionnaly, other posts of interest:
- Marketing in the software center: [http://askubuntu.com/a/103407](http://askubuntu.com/a/103407)
- Directories developers can put their files into: [http://askubuntu.com/a/158732](http://askubuntu.com/a/158732) (but I don&#8217;t know if it applies to closed-source apps.)
- Linking to an app in the software center: [http://askubuntu.com/a/100307](http://askubuntu.com/a/100307) (can be useful in a demo.)

---

