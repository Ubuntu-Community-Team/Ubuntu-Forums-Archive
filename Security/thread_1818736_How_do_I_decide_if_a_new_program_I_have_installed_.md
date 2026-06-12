---
title: "How do I decide if a new program I have installed is malware or not?"
date: 2011-08-05
forum: Security
---

### Post by arroy_0209 on 2011-08-05
In Ubuntu 10.04 LTS, I have downloaded and installed texlive (2011). They have issued the following warnings:
 
1. "To the best of our knowledge, the core TEX programs themselves are (and always have been) extremely robust. However, the contributed programs in TEX Live may not reach the same level, despite everyone’s best efforts. As always, you should be careful when running programs on untrusted input; for maximum safety, use a new subdirectory."
 
What does this exactly mean? The installed program has already created own directories and subdirectories (e.g. /usr/local/texlive/2011/bin/i386-linux). Am I supposed to create a new subdirectory in home to write files and run latex program? Exactly how do I know that the downloaded and installed program is not malicious?
 
2. "Finally, TEX (and its companion programs) are able to write files when processing documents, a feature that can also be abused in a wide variety of ways. Again, processing unknown documents in a new subdirectory is the safest bet." 
 
Can anybody please explain what is implied by "a feature that can also be abused in a wide variety of ways". How do I know in case something bad had really happened?

---

### Post by bodhi.zazen on 2011-08-05
Sounds as if the application has a number of known security holes or exploits which are not full disclosed or patched.

Although many applications have vulnerabilities, I would not use such an application as the one you describe, but you will need to decide for yourself.

Perhaps confine it with apparmor ?

Did the application come from the Ubuntu repositories ?

You should be fine if you simply remove it and use an alternate application.

If the application is in the Ubuntu Repositories , then I would be much less concerned and ask your question on Launchpad.

---

### Post by HermanAB on 2011-08-06
1. Only install stuff from the repos.
2. Google the reputation of external programs.
3. Watch the logs.
4. Watch the network.

---

### Post by arroy_0209 on 2011-09-03
Thanks for your suggestions. I'd like to "confine" it with apparmor as bodhi.zazen says. But have no idea how to do that. Can anybody please suggest how to do that? I need a thorough manual for apparmor application at basic level. So far I am unable to find any such source. Please help.

---

### Post by handy on 2011-09-03
> **arroy_0209 said:**
> Thanks for your suggestions. I'd like to "confine" it with apparmor as bodhi.zazen says. But have no idea how to do that. Can anybody please suggest how to do that? I need a thorough manual for apparmor application at basic level. So far I am unable to find any such source. Please help.

I just Scroogled "how to use apparmor" & this is the first thing that came up:

[http://www.overclock.net/linux-unix/517324-tutorial-secure-ubuntu-apparmor.html](http://www.overclock.net/linux-unix/517324-tutorial-secure-ubuntu-apparmor.html)

This was the 4th:

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

This was the 5th:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

6th:

[https://help.ubuntu.com/8.04/serverguide/C/apparmor.html](https://help.ubuntu.com/8.04/serverguide/C/apparmor.html)

7th:

[http://www.ubuntugeek.com/detailed-tutorial-about-apparmor-for-ubuntu-users.html](http://www.ubuntugeek.com/detailed-tutorial-about-apparmor-for-ubuntu-users.html)

***[edit:]** This last one links to bodhi.zazen's "Introduction to Apparmor" that is a sticky in this Security Discussions sub-forum.*

---

### Post by Bachstelze on 2011-09-06
> **bodhi.zazen said:**
> Sounds as if the application has a number of known security holes or exploits which are not full disclosed or patched.

Although many applications have vulnerabilities, I would not use such an application as the one you describe, but you will need to decide for yourself.

Perhaps confine it with apparmor ?

Did the application come from the Ubuntu repositories ?

You should be fine if you simply remove it and use an alternate application.

If the application is in the Ubuntu Repositories , then I would be much less concerned and ask your question on Launchpad.

I am surprised to read this from you. The warnings pasted by OP are just common sense warnings to be careful when handling untrusted data, and could apply to any program. Looking at the recent USNs, texlive does not seem to have more vulnerabilities than the average package, so your message borders on FUD.

---

