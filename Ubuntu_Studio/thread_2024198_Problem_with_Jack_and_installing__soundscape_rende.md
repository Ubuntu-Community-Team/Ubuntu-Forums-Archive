---
title: "Problem with Jack and installing  soundscape renderer"
date: 2012-07-13
forum: Ubuntu Studio
---

### Post by Gusss on 2012-07-13
The program soundscape renderer needs the "JACK Audio Connection Kit" . However when I try to install it it says Jack is already installed, but when I try and install soundscape renderer it says it cant find Jack :
> 
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
You appear to have at least one existing installation of JACK.

Complete or partial JACK installs exist in: /usr/lib

Installing this version will leave at least one of these
existing installations installed and this will probably break
JACK on your machine. 

Before building, you should first remove the existing JACK
installation(s). 

Alternatively use ./configure --prefix=... to force overwriting
the existing install.

WARNING: ON ANY DEBIAN-DERIVED DISTRIBUTION (Debian, Ubuntu etc)
CHANGING THE INSTALLATION PREFIX WILL NOT PRODUCE A WORKING JACK
INSTALL. Please contact the distribution packager for JACK and
ask them to fix their packaging.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

When I try and install ssr ~I get :

>  checking for JACK... no
configure: error: Package requirements (jack >= 0.118.0) were not met:

No package 'jack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Should I uninstall jack to install this connection kit and if so where is jack installed in ubuntu studio anyway. If not how do I tell ssr where jack is - which file do I edit and again - where is jack located ????

---

### Post by CrocoDuck on 2012-07-13
Hi. As you are on ubuntu studio your user should be in the audio group, but is better to check anyway:

```
groups
```

If your user isn't in the audio group, check if audio group exists:

```
grep -w audio /etc/group |cut -d: -f1
```

the output has to be audio. If so:

```
sudo adduser your-user-name audio
```

jack should be installed in /usr/lib, the jackd daemon in /usr/bin . How are you installing ssr?

---

### Post by Gusss on 2012-07-13
> **CrocoDuck said:**
> Hi. As you are on ubuntu studio your user should be in the audio group, but is better to check anyway:

```
groups
```

If your user isn't in the audio group, check if audio group exists:

```
grep -w audio /etc/group |cut -d: -f1
```

the output has to be audio. If so:

```
sudo adduser your-user-name audio
```

jack should be installed in /usr/lib, the jackd daemon in /usr/bin . How are you installing ssr?

Thanks for the prompt reply ! - I have now added myself to the audio group - but am still getting the same responses posted in my first post.

---

### Post by Gusss on 2012-07-13
I am installing SSR with ./configure
make
make install
but not getting past ./configure at the moment.
Jack is installed (well ctr jack in the softwarecentre is anyway)

---

### Post by Gusss on 2012-07-13
ssr .tar 0.3.3 can be found here :

[https://dev.qu.tu-berlin.de/projects/ssr/files](https://dev.qu.tu-berlin.de/projects/ssr/files)

---

### Post by CrocoDuck on 2012-07-13
EDIT: sorry, I did not read well. Wait, I try to build ssr.

---

### Post by Gusss on 2012-07-13
you will probably need to make sure you look at the pdf document "SoundScapeRenderer-0.3.3-manual.pdf" in the doc folder. Lots of dependencies and packages need to be installed first namely :

 JACK Audio Connection Kit [4]
- FFTW3 compiled for single precision (fftw3f) version 3.0 or higher [5]
- libsndfile [6]
- Ecasound [7]
- Trolltech&#8217;s Qt 4.2.2 or higher with OpenGL (QtCore, QtGui and QtOpenGL) [8]
- libxml2 [9]
- Boost.Asio [10], included since Boost version 1.35.

[4] Paul Davis et al. JACK Audio Connection Kit. [http://jackaudio.org](http://jackaudio.org).
[5] Matteo Frigo and Steven G. Johnson. FFTW3. [http://www.fftw.org](http://www.fftw.org).
[6] Erik de Castro Lopo. libsndfile. [http://www.mega-nerd.com/libsndfile](http://www.mega-nerd.com/libsndfile).
[7] Kai Vehmanen. Ecasound. [http://eca.cx/ecasound](http://eca.cx/ecasound).
[8] Trolltech. Qt4. [http://doc.trolltech.com/4.2](http://doc.trolltech.com/4.2).
[9] Daniel Veillard. Libxml2. [http://xmlsoft.org](http://xmlsoft.org).
[10] Boost C++ Libraries. [http://www.boost.org](http://www.boost.org).


Thanks again for your help - this is driving me crazy !

---

### Post by CrocoDuck on 2012-07-13
I should try to install libjack-dev or libjack-jackd2-0, but I can't because dependencies issues. In the manual is written that we need development libs, so maybe here we have te core of the issue. Have a try to install it, **if your dependencies lets to do it**. The installation should bring to us a file named jack.pc in /usr/lib/pkgconfig . You can search for this with:

```
locate jack.pc
```

If you find a different path from /usr/lib/pkgconfig repost it.

---

### Post by Gusss on 2012-07-13
> **CrocoDuck said:**
> I should try to install libjack-dev or libjack-jackd2-0, but I can't because dependencies issues. In the manual is written that we need development libs, so maybe here we have te core of the issue. Have a try to install it, **if your dependencies lets to do it**. The installation should bring to us a file named jack.pc in /usr/lib/pkgconfig . You can search for this with:

```
locate jack.pc
```

if you find a different path than /usr/lib/pkgconfig try:

```
PKG_CONFIG_PATH=the-path-you-found
```

or

```
./configure PKG_CONFIG_PATH=the-path-you-found
```

didnt work im afraid

---

### Post by CrocoDuck on 2012-07-13
> **Gusss said:**
> didnt work im afraid

Damm it... so:

```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
```

to reset the variable on standard value.

How about the output of

```
locate jack.pc
```

?

---

### Post by Gusss on 2012-07-13
dew@ubuntu:~$ sudo apt-get install libjack-dev
[sudo] password for dew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libjack-dev : Depends: libjack0 (= 1:0.121.0+svn4538-3ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
dew@ubuntu:~$

---

### Post by Gusss on 2012-07-13
Its OK did it !
you were right though I had to install another dependancy libjack0.
Now I have a new problem :

checking for boost/asio.hpp... yes
checking for boost_system library... not found!
checking for boost_thread library... not found!
checking for library containing pthread_join... none required
configure: error: ip-interface (network (TCP/IP) interface) not available! Use --disable-ip-interface to deactivate.

---

### Post by CrocoDuck on 2012-07-13
> **Gusss said:**
> Its OK did it !
you were right though I had to install another dependancy libjack0.
Now I have a new problem :

checking for boost/asio.hpp... yes
checking for boost_system library... not found!
checking for boost_thread library... not found!
checking for library containing pthread_join... none required
configure: error: ip-interface (network (TCP/IP) interface) not available! Use --disable-ip-interface to deactivate.

It looks we have to install boost.asio libraries, as we done for jack. Try with libboost-dev or libboost-all-dev.

---

### Post by Gusss on 2012-07-13
> **CrocoDuck said:**
> It looks we have to install boost.asio libraries, as we done for jack. Try with libboost-dev or libboost-all-dev.

that did it - "sort of" when I  "make" it says :

> ./gui/qopenglplotter.h:193:5: error: &#8216;GLUquadricObj&#8217; does not name a type
posixpathtools.h: In function &#8216;bool posixpathtools::getcwd(std::string&)&#8217;:
posixpathtools.h:141:27: warning: ignoring return value of &#8216;int fchdir(int)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
make[2]: *** [ssr-controller.o] Error 1
make[2]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dew/Desktop/ssr-0.3.3/src'
make: *** [all-recursive] Error 1


and although config got to the end this time (hurray) it said :

> checking various header files for InterSense tracker support... see below
checking isense.h usability... no
checking isense.h presence... no
checking for isense.h... no
checking types.h usability... no
checking types.h presence... no
checking for types.h... no
configure: WARNING: --enable-intersense (InterSense tracker support) requested but not available!
configure: creating ./config.status

though the InterSense thing  might just be a red herring

---

### Post by CrocoDuck on 2012-07-13
> **Gusss said:**
> that did it - "sort of" when I  "make" it says :




and although config got to the end this time (hurray) it said :



though the InterSense thing  might just be a red herring

At page 14 of the manual you see how to build ssr with InterSense support, but it should be facultative... I'm reading the headers, but I cannot point out the issues... Keep on working after a reboot, it may restore some default variable/setting or update infos after so many installations... So sorry but I feel like I run out of ammo :sad:...

---

### Post by Gusss on 2012-07-13
> **CrocoDuck said:**
> At page 14 of the manual you see how to build ssr with InterSense support, but it should be facultative... I'm reading the headers, but I cannot point out the issues... Keep on working after a reboot, it may restore some default variable/setting or update infos after so many installations... So sorry but I feel like I run out of ammo :sad:...

You've been a great help - cheers :KS

---

### Post by CrocoDuck on 2012-08-06
Solution in this thread: [http://ubuntuforums.org/showthread.php?t=2024431](http://ubuntuforums.org/showthread.php?t=2024431)

---

