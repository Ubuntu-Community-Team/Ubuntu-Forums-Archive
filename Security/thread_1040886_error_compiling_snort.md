---
title: "error compiling snort"
date: 2009-01-16
forum: Security
---

### Post by newbux on 2009-01-16
hi i am trying to install and compile snort per the tutorial above. and when i went to compile snort i got errors. 

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472) 

and i think i did everything correctly and i compiled this application snort and received a error message i am at a loss of what to do now can you help out some of it compiled but thier was this error at the end

terminal code in tutorial:

cd /usr/src/snort-2.8.3
./configure -enable-dynamicplugin --with-mysql
make
make install

error:

In function ‘open’,
inlined from ‘server_stats_save’ at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[4]: *** [server_stats.o] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow/portscan'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3.1/src'
make: *** [install-recursive] Error 1

ive posted in upper big OP but with no luck thanks

---

### Post by G0rt3k on 2009-01-22
On your
```
<path_to_snort_source>/src/preprocessors/flow/portscan/server_stats.c 
```

change this line:
```
fd = open(filename, O_CREAT|O_TRUNC|O_SYNC|O_WRONLY);
```

with this one:
```
fd = open(filename, O_CREAT, S_IRUSR|S_IWUSR|O_TRUNC|O_SYNC|O_WRONLY);
```

Source of this information:
```
http://www.snort.org/reg-bin/forums.cgi?forum_id=4&topic_id=6119
```

After this change, the compilation works.

Hope it help you!
Regards,
G0rt3k

---

### Post by digitmonk on 2009-04-01
G0rt3k

Thank you.  The fix worked.

---

### Post by dhughes on 2009-09-08
About 

```
<path_to_snort_source>/src/preprocessors/flow/portscan/server_stats.c
```

 For me the trail ends at *<path_to_snort_source>/src/preprocessors* there isn't any 'flow' folder, there are lots of other folders, which I looked into, but no flow. No portscan folder and I when I grepped for "server_stats.c" in the snort directory it didn't find it, I'll keep looking.

 The Snort link you submitted is dead as well, no redirect.

 Thanks for the effort, but I'm at a dead end.

**edit**: ignore all that, I re-ran 'make install' again only I used 'sudo make install' , the guide I followed didn't mention using sudo before 'make install', I had a bad feeling about that and should have followed my instincts! There weren't any errors after using sudo for 'make install'.

---

### Post by fetanyl on 2010-01-23
hi i am new to ubuntu and linux in general and when i am trying to compile snort i get an error.

i am in /usr/share/doc/snort i could not find my plugins so i have swrx-snort-plugin-pack-0.2.0.tar.gz

well when i type in ./configure -enable-dynamicplugin --with-mysql i get the error 
bash: ./configure: No such file or directory 

thank you for the help

---

### Post by cariboo on 2010-01-23
If you there isn't a file called configure in the directory you're in, the command won't work.

Is there a reason why you are trying to compile from source, instead of installing snort from the repositories?

---

### Post by fetanyl on 2010-01-24
i re-installed snort from the repositories idk why i did not do this in the first place im slowly making progress on setting this up its a bit hard being new to ubuntu and linux in general (im on day number 4 of using this). thanks for the help chief.

i know this is probably a dumb question but if i installed snort from the repository i am assuming that i do not have to write a script to start snort correct?
(i am just following the steps from [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472) )

---

### Post by krodrigue on 2010-04-29
I am trying to add snort using the sticky, I got to this part:

./configure -enable-dynamicplugin --with-mysql

 ERROR!  Libpcap library/headers (libpcap.a (or .so)/pcap.h)
   not found, go get it from [http://www.tcpdump.org](http://www.tcpdump.org)
   or use the --with-libpcap-* options, if you have it installed
   in unusual place.  Also check if your libpcap depends on another
   shared library that may be installed in an unusual place
Do I just need to wget the libpcap from their site?

---

### Post by bodhi.zazen on 2010-04-29
You probably need to install the libcap development package:

```
sudo apt-get install libcap-dev
```

---

### Post by abrahampalace on 2010-12-10
my probelm is about libdnet, it make i can't ./configure my snort
i'm very stuck with it..
please help, i've been try to apt-get install libdnet-dev and it's successfull

---

### Post by cariboo on 2010-12-11
I would suggest you use aptitude to install the libnet-dev virtual package. I'm running Natty, so your result may be slightly different, when I type:

```
sudo aptitude install libnet-dev
```

I get the following result:

```
sudo aptitude install libnet-dev
[sudo] password for cariboo: 
Note: selecting "libnet1-dev" instead of the
      virtual package "libnet-dev"
The following NEW packages will be installed:
  libnet1{a} libnet1-dev 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 176 kB of archives. After unpacking 729 kB will be used.
Do you want to continue? [Y/n/?]
```

As you can see from the above output the package is now called libnet1-dev.

**Note:** If you are running maverick you'll have to install aptitude, as it is no longer installed by default.

---

