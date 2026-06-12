---
title: "Phoronix Test Suite"
date: 2010-03-02
forum: The Cafe
---

### Post by katie-xx on 2010-03-02
[SIZE=2][COLOR=Magenta]I didnt want to go off topic in Handy's super ATI driver thread hence this one.
Handy mentioned the Phoronix Test Suite in his post and Ive taken a look at the website
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)
Can anyone give an overview of this? Is it worth the download?

Thanks
Kate[/COLOR][/SIZE]

---

### Post by phrostbyte on 2010-03-02
It's probably the most complete general purpose benchmarking suite for Linux.

---

### Post by katie-xx on 2010-03-02
> **phrostbyte said:**
> It's probably the most complete general purpose benchmarking suite for Linux.
[SIZE=2]
Thanks. Does it use test data or a standard suite of tests ?
It does seem to take a lot of room up.
Thanks again

Kate[/SIZE]

---

### Post by mtippett on 2010-03-02
(Full disclosure - I am one of the founders for the project).

Phoronix Test Suite is a test execution framework.  The tests themselves are structured as "Suites" or "Profiles".  A Suite usually has a theme (like gaming).  A Profile is associated with an application (like Unigine Tropics).

Depending on what you are testing, there may be a lot of data to download.  For some tests there are simply small downloads, for others it's hundreds of megabytes.  But in general, the download is matched by what you would download for the application anyway.

What are you wanting to test?

---

### Post by fatality_uk on 2010-03-03
It's the ONLY test suite that can do anything other than measure disk activity.

---

### Post by 3rdalbum on 2010-03-03
Phoronix Test Suite is great. It's a serious benchmarking tool, but it also helped me check my CPU cooling with 'cpuburn' and running 'watch sensors' in the terminal; and it helped me figure out that my RAM was faulty (I ran one of the memory bandwidth tests and the computer kept freezing).

I also compare graphics cards by running Unigine Tropics in Phoronix Test Suite.

I haven't even scratched the surface of what PTS does, but it's an awesome open-source benchmarking tool. If you think you'd be interested in it at all, you should explore its fullness.

P.S. mtippett, next time you're in my home city I'll buy you a beer for helping me with my memory problem :-)

---

### Post by katie-xx on 2010-03-03
> **mtippett said:**
> (Full disclosure - I am one of the founders for the project).
Phoronix Test Suite is a test execution framework.  The tests themselves are structured as "Suites" or "Profiles".  A Suite usually has a theme (like gaming).  A Profile is associated with an application (like Unigine Tropics).
Depending on what you are testing, there may be a lot of data to download.  For some tests there are simply small downloads, for others it's hundreds of megabytes.  But in general, the download is matched by what you would download for the application anyway.
What are you wanting to test?
[SIZE=2]
Thanks for replying. Where else could you go to get a response from a project founder? Fantastic.
I hadnt heard of the Phoronix Suite until I read Handy's thread. he has made a lot of
good quality posts on here and I was impressed when he said he found the suite educational.
So I wanted to find out exactly what the suite was capable of and what, if anything I could hope to get out of it.

Thanks to all the answers, here, and from reading the website overview I now have a much better idea and I think I will download and investigate over the weekend.

You ask what it is I want to test.
 Well, Im actually keen to learn as much as I possibly can about all things Linux and in building up a comprehensive knowledge base of my own so Im basically interested in testing everything I can :)

So Im looking forward to this weekend and the opportunity to explore your suite.

Thanks

Kate
[/SIZE]

---

### Post by tgalati4 on 2010-03-03
It's best feature is the ability to upload your results and compare to other machines.

It uses a lot of space because it downloads rather large files and filesets for compilation tests, encoding tests, playback tests, etc.  You can always delete them when you are done.  Once your run a complete set of benchmarks, you can save the html result files for future reference then delete all of the tests and test data.

---

### Post by mtippett on 2010-03-03
> **katie-xx said:**
> [SIZE=2]
Thanks for replying. Where else could you go to get a response from a project founder? Fantastic.


Well, I didn't come across the thread via searching the forums, it was through a google alert, but I'm still an Ubuntu user since the early days.

> 
...

So I wanted to find out exactly what the suite was capable of and what, if anything I could hope to get out of it.


It can be a lot of things to a lot of people.  In it's bare form, it is just an easy way of testing, gathering and comparing results.  It's then a matter of finding or writing the test profiles that you care about to test what you need to test.  If you are just learning Linux, it's a great tool to look at the endless religious wars in the community...  This filesystem or that filesystem, this distro vs that distro, this video driver vs that video driver.

> 
Thanks to all the answers, here, and from reading the website overview I now have a much better idea and I think I will download and investigate over the weekend.


You can actually install it with most of the recent versions of Ubuntu - ```
sudo apt-get install phoronix-test-suite
```.

> 
So I'm looking forward to this weekend and the opportunity to explore your suite.


Great.  Feel free to contact me [email]matthew@phoronix.com[/email] for more information.

---

### Post by handy on 2010-03-04
My installation was testing games performance it would seem, as it downloaded & installed:

Urban Terror 4.1
OpenArena 0.8.1
World of Padman 1.2
Nexuiz 2.5.2

The installation under these circumstances took up approx' 2GB of HDD space.  (Well worth it imho)

As I keep saying, I wasn't aware that my results could be published on the web, so the name 1st.phoronix.test is somewhat embarrassing. :oops:

Here are the results:

[http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834](http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834)

Which also give you tabs for more info' & the download page.

Thanks mtippett for all your work. :)

---

### Post by katie-xx on 2010-03-07
Hmm ... maybe Im being a little thick. What exactly does one need to download to install this?
Remarkable lack of success here mainly due to a whole load of problems trying to compile.


Kate

---

### Post by phoronix on 2010-03-08
> **katie-xx said:**
> Hmm ... maybe Im being a little thick. What exactly does one need to download to install this?
Remarkable lack of success here mainly due to a whole load of problems trying to compile.


Kate

You just need PHP5-CLI (sudo apt-get install php5-cli) installed and then download the Debian package or .tar.gz version and just install or run it from the directory. PTS should take care of the rest.

-- Michael

---

### Post by descendent87 on 2010-03-17
The phoronix test suite is great, I only wish I could get the gui version to work, seems ubuntu doesn't package php-gtk (hasn't been developed since 2008 from what I can see)

---

### Post by phoronix on 2010-03-18
> **descendent87 said:**
> The phoronix test suite is great, I only wish I could get the gui version to work, seems ubuntu doesn't package php-gtk (hasn't been developed since 2008 from what I can see)

Unfortunately upstream doesn't release often but apparently they claim to still actively be in development. A PHP5 GTK package we made for amd64 Debian/Ubuntu can be found @ [http://phoronix-test-suite.com/misc/php5-gtk2_2.0.1-0_amd64.deb](http://phoronix-test-suite.com/misc/php5-gtk2_2.0.1-0_amd64.deb) And then add extension=php_gtk2.so to your php.ini file afterwards. Or use [http://www.pts-desktop-live.com/](http://www.pts-desktop-live.com/) as an easy way to play with PTS and/or the GUI.

---

### Post by descendent87 on 2010-03-18
Brilliant, thanks a lot
EDIT: Package doesn't work, get an error saying:
```
PHP Warning: PHP Startup: php-gtk: Unable to initialize module
Module compiled with module API=20060613
PHP compiled with module API=20090626
These options need to match
in Unknown on line 0
PHP Fatal error: Class 'GtkWindow' not found in /usr/share/phoronix-test-suite/pts-core/objects/gtk/pts_gtk_window.php on line 24
```

Also is softpedia the only mirror for pts-desktop-live? As it's 1.4 GB and I can never seem to get over 30KB/sec from that site so the download will take over 12 hours for me

---

### Post by skeetre on 2010-04-15
I have the same problem.
```
PHP Warning:  PHP Startup: php-gtk: Unable to initialize module
Module compiled with module API=20060613
PHP    compiled with module API=20090626
These options need to match
 in Unknown on line 0
PHP Fatal error:  Class 'GtkWindow' not found in /usr/share/phoronix-test-suite/pts-core/objects/gtk/pts_gtk_window.php on line 24

```

---

### Post by phoronix on 2010-04-15
> **descendent87 said:**
> Brilliant, thanks a lot
EDIT: Package doesn't work, get an error saying:
```
PHP Warning: PHP Startup: php-gtk: Unable to initialize module
Module compiled with module API=20060613
PHP compiled with module API=20090626
These options need to match
in Unknown on line 0
PHP Fatal error: Class 'GtkWindow' not found in /usr/share/phoronix-test-suite/pts-core/objects/gtk/pts_gtk_window.php on line 24
```

Also is softpedia the only mirror for pts-desktop-live? As it's 1.4 GB and I can never seem to get over 30KB/sec from that site so the download will take over 12 hours for me


Unfortunately PHP's API broke with Lucid now... Though by the time PTS 2.6.0 is out hopefully I'll get around to making a new Debian package of PHP-GTK.

There are PTS Desktop Live torrents if you look around, but sadly right now Softpedia is the only HTTP mirror.

---

### Post by handaxe on 2010-05-24
To clarify, does PTS 2.6.0 (released yesterday) work only with a Lucid compiled version of php5-gtk rather than an older one?  

Did you perhaps get around to compiling that deb you (perhaps foolishly :) ) mentioned.....?

---

### Post by phoronix on 2010-05-24
> **handaxe said:**
> To clarify, does PTS 2.6.0 (released yesterday) work only with a Lucid compiled version of php5-gtk rather than an older one?  

Did you perhaps get around to compiling that deb you (perhaps foolishly :) ) mentioned.....?

PTS 2.6.0 isn't dependent upon any specific compilation of PHP5-GTK. However, Lucid's PHP will only work with a PHP5-GTK binary module that is compatible with its ABI. The Debian PHP5-GTK package I previously had available is not compatible with that ABI. It's a general PHP issue and not something specific to PTS.

I have built a 32-bit PHP5-GTK for Lucid, but haven't yet gotten around to building a 64-bit version -- probably a couple days until I find the time.

---

### Post by handaxe on 2010-05-24
Damn, you're fast - my return key was still warm.....

Thanks for the clarification.  An URL for that 32 bit deb if you will, please.

rgrds,

HA

---

### Post by jk-menifee on 2010-05-28
Hello all,

I'm planning to build a new Linux box soon and I wanted to benchmark my current one. It looks like Phoronix Test Suite is the way to go, and I found this link to a basic benchmarking suite which I am dying to try out:

[http://global.phoronix-test-suite.com/?k=profile&u=mendieta-4549-6954-342](http://global.phoronix-test-suite.com/?k=profile&u=mendieta-4549-6954-342)

I'm having the same problems as the folks above, making Phoronix work in Lucid Lynx, and getting PHP errors. But perhaps my problem is a little different. Here are my symptoms:

- If I type phoronix-test-suite on the teminal, I get:
"PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown on line 0"
- The program continues, with the next problem being a segmentation fault.
- If I try to do anything useful such as run a benchmark:

```
$phoronix-test-suite benchmark mendieta-4549-6954-342
...
Current Test Identifiers:
- Phenom X3, 2.3 Ghz, ddr2-800

Enter a unique name for this test run: dell

###########################################
If you wish, enter a new description below.
Press ENTER to proceed without changes.
###########################################

Current Description: Light, overall system performance suite

New Description: 
Segmentation fault


SciMark:
      scimark2 [Computational Test: Composite]
      Test Run 1 of 4
      Expected Trial Run Count: 4
            Started Run 1 @ 18:13:14
            Started Run 2 @ 18:13:47
            Started Run 3 @ 18:14:20
            Started Run 4 @ 18:14:50
sh: /home/myth/.phoronix-test-suite/: Permission denied
sh: 273.50:PHP: not found
sh: 271.80:PHP: not found
sh: 266.90:PHP: not found

      Test Results:
            PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown on line 0
273.50
            PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown on line 0
271.80
            PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown on line 0
266.90
            PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown on line 0
263.29

      Average: 0 Mflops
```

Most of the above discussion, I believe is related to the GUI; perhaps I'm incorrect but it seems to me php-gtk would not be relevant for the command line. I did confirm I have the current version of PHP5-CLI installed but I'm still getting these errors.

Any advice?

John

---

### Post by jk-menifee on 2010-05-28
What do you know. Editing /etc/php5/cli/conf.d/mcrypt.ini to change the # to // fixed the PHP problem and I'm off and running. I still get segmentation faults though but the light test suite ran to completion with all output nicely formatted. I still get the segmentation faults though; and the fio test "exited with a non-zero exit status." I'll have to look into that. But otherwise I'm quite pleased that one tiny little edit took care of it.

---

### Post by alfmarius on 2010-09-06
> **jk-menifee said:**
> What do you know. Editing /etc/php5/cli/conf.d/mcrypt.ini to change the # to // fixed the PHP problem and I'm off and running. ...... But otherwise I'm quite pleased that one tiny little edit took care of it.

This little warning was very annoying! I got it on a fresh install of Ubuntu 10.04.1 LTS and using apt-get to install php5.

Thanks a lot for this fix, since no one else commented after you I hope it's a "valid" fix :)

---

### Post by waperboy on 2010-10-05
I'm having a different problem with the test-suite. I get the gui up, and I can select and download test-suites. I can click on run, and enter parameters. In the console, it says that it's running the test, but it's not doing anything. It prints "Test results", but there are no results.

To sum up, it goes through the motions of running the test, but it's not actually running the test. Then it prints out empty test result.

Sound familiar to anyone?

(Ubuntu 10.04 64 bit).

---

