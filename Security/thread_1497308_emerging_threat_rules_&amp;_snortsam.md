---
title: "emerging threat rules &amp; snortsam"
date: 2010-05-30
forum: Security
---

### Post by Lori700698 on 2010-05-30
When I upgraded to 10.4LT I agreed to something that stopped snort, after days decided to just re-do with new snort version.  Used bodhi.zazen's MySql instruction version (which is what I used in the past) Everything went pretty well except for figuring out that I needed to delete all the lib_sfdynamic_preprocessor_example?? files (I also deleted all the lib_sfdynamic_example?? files too just to be safe).  Used my original Oinkmaster with updated rules version and downloaded the emerging threats too (as I had in the past) and snort won't run with some of the emerging threat rules because it's lookning for snortsam (fwsam).  I read up and snortsam looks like a good idea (if I'm wrong somebody just let me know)

Here's my issue...sorry if this seems dumb, but I really don't understand, the snortsam directions are HORRIBLE, the snortsam src looks like a windows file when unpacked with all the .dll files(but they say for all OS's), it builds but you need to copy the binary to /usr/local/bin (what in ubuntu would be a binary?). 

the snortsam-patch-2.8.tar.gz won't unpack and the Snort 2.8.6 patch is a file, not a package (have no clue where to put it or what to call it if I got the 2.8.tar.gz to unpack so I could build it)

Any ideas?

Thanks
Lori

---

### Post by bodhi.zazen on 2010-05-31
I have not used snortsam, but detailed instructions are here:

[http://doc.emergingthreats.net/bin/view/Main/SnortSamINSTALL](http://doc.emergingthreats.net/bin/view/Main/SnortSamINSTALL)

Additional documentation is here:

[http://doc.emergingthreats.net/bin/view/Main/SnortSamDocumentation](http://doc.emergingthreats.net/bin/view/Main/SnortSamDocumentation)

My guess is you may have downloaded the windows files, try the linux files.

A very nice alternate (IMO) is psad + fwsnort.

[http://bodhizazen.net/Tutorials/psad/](http://bodhizazen.net/Tutorials/psad/)

---

### Post by Lori700698 on 2010-05-31
bodhi.zazen
Thanks for the psad + fwsnort tutorial, I need to give that a try, although I don't seem to be under rouge attacks at the moment, but I'm well aware that it could start at any time. Every time I get a hiccup on my system and I have to tinker to get everything running again I do seem to learn more, security is complicated and very confusing at times. Do you use the emerging threat rules?  If so, are you using fwsnort to tie in the block rule sets?  I think it could be done... I may need some help to try it.

For the record I double checked this morning since my "frazzled mode" came down a couple of notches and yes I did use the right source, looks like the source is an "all inclusive" with patches geared to specific OS's.  Guess I'm a tad miffed over the package not un-taring then the odd plug-in-patch file.  The directions are really old and don't explain much.

Thanks so much
Lori

---

### Post by bodhi.zazen on 2010-06-01
> **Lori700698 said:**
> bodhi.zazen
Thanks for the psad + fwsnort tutorial, I need to give that a try, although I don't seem to be under rouge attacks at the moment, but I'm well aware that it could start at any time. Every time I get a hiccup on my system and I have to tinker to get everything running again I do seem to learn more, security is complicated and very confusing at times. Do you use the emerging threat rules?  If so, are you using fwsnort to tie in the block rule sets?  I think it could be done... I may need some help to try it.

For the record I double checked this morning since my "frazzled mode" came down a couple of notches and yes I did use the right source, looks like the source is an "all inclusive" with patches geared to specific OS's.  Guess I'm a tad miffed over the package not un-taring then the odd plug-in-patch file.  The directions are really old and don't explain much.

Thanks so much
Lori

It is unfortunate when the Documentation fails to keep pace with development.

I use emerging threats and have not had any major problems with it, either with snort or psad.

If you are new to snort, keep in mind snort gives a fair amount of false negatives and you probably should fine tune your rule set before you start automatically blacklisting an ip address simply because a snort alert is generated. Personally I watch BASE .

---

