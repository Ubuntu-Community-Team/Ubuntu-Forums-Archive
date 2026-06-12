---
title: "Development idea: new firefox removal integration"
date: 2007-04-24
forum: Ubuntuzilla
---

### Post by nanotube on 2007-04-24
aysiu has a simple "removenewfirefox" script on his site ([http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)) that i think could do well with some integration into the ubuntuzilla project. 

first, i think i would like to spiff it up a bit before including it into ubuntuzilla (ask the user whether he wants to actually delete /opt, or just change the links, check error codes before moving on). also to include some warnings that if the user is downgrading from 2.0 to 1.5, the profile may not be usable by the old firefox anymore.

i am also thinking to make the install script accept a command-line argument "-remove" which would remove, or "-install" which would install, so that the user doesn't have to download extra scripts, and so as to make it clear that it only works if you used the script to install. any thoughts about this, aysiu (and anyone else who cares)?

---

### Post by aysiu on 2007-04-24
That sounds like a great idea, nanotube! Integration is good.

By the way, I've updated my links on the Psychocats site to point to the new Ubuntuzilla website.

I'm also phasing out [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

The sidebar on Psychocats now points to Ubuntuzilla website, and I'll start referring people there. I may even change [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) to redirect to Ubuntuzilla's Firefox anchor.

---

### Post by nanotube on 2007-04-24
i think your ubuntu/firefox page could be of some use yet for the next couple of weeks, especially as you or i go about editing the ubuntuzilla site, it could serve as a reference. so rather than just cleaning it out, maybe just put a link at the top that says "this project is now hosted at ___, info below could be outdated".

thanks for your vote of confidence about removal. i will get right on with implementation within the next few days. :)

---

### Post by nanotube on 2007-04-24
ok, attached is the version of the firefox script that can install and remove the mozilla build of firefox (use '-h' command line option for usage instructions).

please test, give comments, suggestions. 

testers in addition to aysiu are quite welcome to give it a shot! :)

if this works, without problems, i will do the same for the thunderbird script.

also, since the script does install and remove, would it make sense to rename it to something like "ubuntuzillafirefox.sh"? or shall we just stick with the old name?

---

### Post by aysiu on 2007-04-25
I tested installation and removal--worked a charm!

---

### Post by nanotube on 2007-04-25
> **aysiu said:**
> I tested installation and removal--worked a charm!

ok, in that case, i'm uploading this version to the live site.

let me know when you have some thunderbird testing results.

---

