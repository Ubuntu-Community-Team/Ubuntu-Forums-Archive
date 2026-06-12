---
title: "Firefox extensions"
date: 2008-09-14
forum: Virtualisation
---

### Post by Zynaps on 2008-09-14
I just made a post here ([http://ubuntuforums.org/showthread.php?p=5787504#post5787504](http://ubuntuforums.org/showthread.php?p=5787504#post5787504)) regarding the problems loading Cooliris in firefox, because there is no linux version of the extension.

This got me thinking (maybe not a good thing) about the bigger picture.

The nature of the problem on a wider scale that I can see is that some (many?) Firefox extensions rely very heavily on DLL's.  In order to be able to use the features offered by such extensions, if the problem were tackled on a per-extension basis, one could either:
1. Write a new program that mimics the behavior of the desired app (time consuming, there's thousands of potential projects)
2. Try and petition the developers to make a linux port (with varying levels of success I can imagine)
3. Try and reverse engineer the extension (probably time consuming, with mixed results)
4. Forget about it and do without the feature (boring and unfair)
5. A mixture of all of the above.

I don't know much about linux (yet) but I have heard of things like wine and vmware etc, so I know it's possible to somehow execute windows binaries, capture calls to windows libraries and so forth.

Rather than addressing each individual extension, could the whole class of firefox incompatibility problems be addressed with a single project that extends firefox on linux to provide support for windows based extensions?  Could windows based extensions be installed as is, and some layer take any windows specific code and put it through an emulator or some such thing?  I.E. for the end user the once agonizing process of the above 5 options now becomes:

1. Install the super-duper-firefox-windowmasher extension
2. Install whatever windows based extensions we feel like, without having to worry about porting them, or heckling developers for a linux version, or writing a whole new app from the ground up.
3. User experience enhanced thanks to invisible forces making life easier.

Just a thought - like I said I am new to linux, but if something like this could be attempted would it be a huge undertaking, could existing tools be leveraged to make this happen, would it be worthwhile?

---

