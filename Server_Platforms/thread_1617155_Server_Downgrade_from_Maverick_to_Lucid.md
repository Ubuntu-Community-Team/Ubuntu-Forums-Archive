---
title: "Server Downgrade from Maverick to Lucid"
date: 2010-11-09
forum: Server Platforms
---

### Post by karthikencore on 2010-11-09
Hi There

I'm new to Ubuntu and trying to setup a server for my home office, But I heard that using Maverick is not suggested for office purpose and asked me to use Lucid instead. 

Can you guy help me with a question? I would like to know which is the best way to this. Should I download the Lucid version install it or do direct downgrade to Lucid?

Thanks

---

### Post by koenn on 2010-11-10
debian-based systems are hard to downgrade  it's not really supported
just start over with a clean install.

---

### Post by Martiini on 2010-11-28
debian / ubuntu downgrade of packages is fully implemented by apt / aptitude 
explained here [http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

search ubuntu forums for "downgrade"

---

### Post by koenn on 2010-11-28
hm, well, yes, lol.
did you actually read that post you linked to ? 
have you ever *tried* a procedure like that ? 

I don't doubt it's *possible*, but it's still hard, and not really supported (1 user's write up of a trial and error that eventually succeeded in 1 specific situation does not make it a supported , generally applicable procedure), and it is obvious frtom that write-ip that you're working against the grain.

In itself, apt-pinning is already quite complex and you need to understand its details quite well to be able to predict the resulting behaviour (eg: the Priority numbers have meaning beyound "higher priority = install it)
That's true in the normal, upgrade-like scenarios. download scenario's are probably even harder to figure out. 

Then (as is also apparent from the post you link), you'll run into a number of problems that will have you manually resolve dependencies and conflicts and circular references,  and you have no guarantee that all packages will actually be replaced by older versions, so you may very well still end up with a mixed system -- with a quite substantial risk of running in to breakage during a future upgrade.


But if you think that's a better approach than spending 30 minutes on a known good installation procedure, restore data, and be done, don't let my opinion stop you.

---

### Post by HugoSerrano on 2010-11-29
I also recommend a fresh clean installation, especial if this is a production server. You may get a buggy machine if you go for the downgrade.

Regards!

---

