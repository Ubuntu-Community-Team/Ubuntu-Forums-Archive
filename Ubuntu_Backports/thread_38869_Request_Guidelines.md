---
title: "**Request Guidelines**"
date: 2005-06-02
forum: Ubuntu Backports
---

### Post by jdong on 2005-06-02
Now that we're official, to maintain package quality and upgradability and to make Backports more stable, we must set down some guidelines for what is allowed to backport.

Currently, these are our rough guidelines:
> 
When to backport, when not to backport (suggestions up for discussion):
    0 **Only packages currently in Ubuntu's development branches are eligible for backporting**
    1   Backports of large, interdepending applications stacks are bad!
    2   New versions can be backported, when they're compatible with already OS and System relevant libraries.
    3   No new libraries, which will "break" or better say, affecting other applications (e.g. libvorbis, libz etc.) unless the update fixes an exploit (Brandon Hale suggests leaving these for the security team).
    4   No changes to language interpreters (python, mono). These could affect existing packages in unexpected ways.
    5   Applications to be backported must have meaningful bug/security fixes or 
features.


With regards to rule 0, the Masters of the Universe guys are responsible for keeping Universe up-to-date. If Backports gets newer than development Universe, there's a risk that when the next release is finalized, Backports won't upgrade to it properly.

---

### Post by Slo Mo Snail on 2005-06-02
0: Ok, but what's about the stuff in hoary-extras?

3: Currently we have backports of libs when some other backport (which otherwise complies to the rules) needs the newer version of the lib but isn't the only application needing this lib. How should this be solved in the future? No backport for the package needing newer libs or is this an exception of the rule?

4: Currently we have a mono backport which is iirc needed by some other packages we have in the backports. So this mono backport and everything depending on it has to be removed?

5: It's imho a matter of opinion whether this rule apply. What is a meaningful bugfix or new feature?

Another question: will there be a "bleeding" and "extras" section like now? I ask this because for example the mono backport could fit in bleeding and the gstreamer-{faac,faad,lame}/transcode/etc packages could fit in extras but all break at least one of the 5 rules

---

### Post by jdong on 2005-06-02
I think everything there now will be kept there, at least in the hoary-backports tree.

Extras will still continue, independently of Backports. (but by the same people)

---

### Post by TravisNewman on 2005-06-02
OK I was worried until you clarified that extras would still be around ;)

Kudos!

---

### Post by RastaMahata on 2005-06-02
sorry, I'm a bit confused here. I hate to waste your time with more questions (that chat log was full of them), but:

Form what I've read, backports is going to be official, thus having a server at ubuntulinux.org. Extras is going to be a thing appart from backports, but still updated? Where will it be hosted? I like extras, as I dont have to compile or get stuff from marillat :(

---

### Post by jdong on 2005-06-03
[QUOTE=RastaMahata]sorry, I'm a bit confused here. I hate to waste your time with more questions (that chat log was full of them), but:

Form what I've read, backports is going to be official, thus having a server at ubuntulinux.org. Extras is going to be a thing appart from backports, but still updated? Where will it be hosted? I like extras, as I dont have to compile or get stuff from marillat :([/QUOTE]
Extras will be hosted just like Backports is currently hosted, on the Backports mirror system. It's going to remain 3rd party and detached from Ubuntu, just like Marillat to Debian.

---

