---
title: "Repository for &quot;Firefox&quot; and &quot;Thunderbird&quot;"
date: 2006-10-17
forum: Repositories &amp; Backports
---

### Post by bhearsum on 2006-10-17
Hi all,

First off I want to say that I am NOT trolling or flaming, so please do not interpret it that way.

I have been thinking about setting up an apt repository to host builds of Firefox and Thunderbird with the official branding switch disabled. I know some people do not want to use the Debian patched builds of Firefox, nor do they want "IceWeasel" or "IceDove".

My school can probably host it, so bandwidth is not an issue. Right now I'm just attempting to gadge interest before going through the trouble of setting things up and doing builds, etc.

Any input (non-flaming) is appreciated.

---

### Post by FastZ on 2006-10-17
I'd rather have a non-Ubuntu version of Firefox.  Only being able to update Firefox when Ubuntu wants me to is annoying.  I like trying out the betas and RCs of Firefox 2.0.  Been running Firefox 2.0 on my Windows machines since beta 1 came out.

---

### Post by aysiu on 2006-10-17
I'm not sure I understand you.

Your repositories would have builds "with the official branding switch disabled"? So how would that be different from IceWeasel?

Do you mean that they would be the official builds or not? If they are the official builds, you don't need a repository. As long as people have them installed, they're self-updating, and there are some damn good scripts out there for installing them.

---

### Post by Shea7993 on 2009-09-03
Uhm im not too sure how much my reply relates to this, at the moment i hate firefox that ships with ubuntu, its giving me serious problems when i follow links, like after the 3rd or 4th link it just wont load pages anymore, so currently i swithced over to chromium that doesnt give me this issue at all, however im looking for an ubuntu repo, the one i got from the homepage isnt working, keep getting error msg

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

im not very clued up but yeah, not working, any help to get me downloading firefox 3.5 and repo for updates?

Thanx

---

### Post by Shea7993 on 2009-09-03
heh, forgot to subscribe =]

---

### Post by running_rabbit07 on 2009-09-03
> **Shea7993 said:**
> Uhm im not too sure how much my reply relates to this, at the moment i hate firefox that ships with ubuntu, its giving me serious problems when i follow links, like after the 3rd or 4th link it just wont load pages anymore, so currently i swithced over to chromium that doesnt give me this issue at all, however im looking for an ubuntu repo, the one i got from the homepage isnt working, keep getting error msg

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

im not very clued up but yeah, not working, any help to get me downloading firefox 3.5 and repo for updates?

Thanx

Try the[ Psychocats]("http://www.psychocats.net/ubuntu/firefox") method, it worked for me. You just download the file from mozilla, place it in your home folder, then copy and paste one happy command and you are done.

---

### Post by wfarr_09 on 2009-12-08
I Know About [Ubuntuzilla]("http://ubuntuzilla.sourcefourge.org") but i'm looking for the official repository for thunderbird-3.0/3.1

please help?? Does anyone know what it is?:KS

---

### Post by nanotube on 2009-12-09
> **wfarr_09 said:**
> I Know About [Ubuntuzilla]("http://ubuntuzilla.sourcefourge.org") but i'm looking for the official repository for thunderbird-3.0/3.1

please help?? Does anyone know what it is?:KS

there is no such thing. if mozilla did host a repository, there would be no need for ubuntuzilla in the first place. :)

---

### Post by tony_clifton on 2009-12-30
There is no official Ubuntu/Mozilla repository for Thunderbird 3.0.  You can get Thunderbird 2.0 from Ubuntu Mozilla Security PPA, or Thunderbird 3.0.1pre from Ubuntu Mozilla Daily PPA, but there is no PPA for regular 3.0.

This was driving me nuts, thanks to this thread I have some form of a solution.

Thank you.

Also, the link to Ubuntuzilla is [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by nanotube on 2009-12-30
by the way, i'm working on setting up a repository with the official mozilla builds repackaged into .debs. stay tuned for the news - or check out the ubuntuzilla testing thread here with to keep track of the progress:
[http://ubuntuforums.org/showthread.php?t=467724](http://ubuntuforums.org/showthread.php?t=467724)

---

### Post by nanotube on 2009-12-31
The Ubuntuzilla repository for mozilla builds of Firefox, Thunderbird, and Seamonkey is now live! The ubuntuzilla website has the details:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

