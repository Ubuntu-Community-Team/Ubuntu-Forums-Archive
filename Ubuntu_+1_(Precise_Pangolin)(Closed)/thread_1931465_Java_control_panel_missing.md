---
title: "Java control panel missing ?"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Stinger on 2012-02-25
Hi

I have installed both icedtea plugin and openjdk, the open source version of Java, but I just cant find the java control panel.

I expected it to be in system-settings, but no.

Does anyone know where to find it or how to launch it from a terminal ?

I need it to see if it has stored the digital signature from my bank.

---

### Post by effenberg0x0 on 2012-02-25
AFAIK, the Java Control Panel was a sun-java application that is not availabe using OpenJDK. I might be wrong here, but I only see it when running sun/oracle java.

Regards,
Effenberg

---

### Post by Stinger on 2012-02-25
Thanks effenberg, you are right, I Googled  a bit and found out that in icedtea openjdk it's called "IcedTea Java 6 Web Start".
It's located in /usr/share/applications but the command to launch it used there was ```
/usr/lib/jvm/java-6-openjdk-i386/bin/javaws %u
```, it didn't work.
BTW my /usr/share/applications folder was a bit messy with a few duplicate entries.

I tried javaws in a terminal a found out that the command from terminal is ```
javaws -viewer
```
The right command in /usr/share/applications should have been ```
/usr/lib/jvm/java-6-openjdk-amd64/bin/javaws -viewer
``` 
What a mess, might file a bug there too.

And that's not all.
I found the digital signature from my bank, the reason why I was looking for it was that I'm prompted to "Always trust content from this publisher" every time I use my bank even though I accept it every time.
With Oracle java it just works and you only have to accept once.
I have a bug filed about it here [bug #941031]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/941031")
You can add yourself to the bug or comment it if you also are affected.
Added a screenshot of my digital signature provider in javaws.

---

### Post by effenberg0x0 on 2012-02-25
> **Stinger said:**
> Thanks effenberg, you are right, I Googled  a bit and found out that in icedtea openjdk it's called "IcedTea Java 6 Web Start".
It's located in /usr/share/applications but the command to launch it used there was ```
/usr/lib/jvm/java-6-openjdk-i386/bin/javaws %u
```, it didn't work.
BTW my /usr/share/applications folder was a bit messy with a few duplicate entries.

I tried javaws in a terminal a found out that the command from terminal is ```
javaws -viewer
```The right command in /usr/share/applications should have been ```
/usr/lib/jvm/java-6-openjdk-amd64/bin/javaws -viewer
```What a mess, might file a bug there too.

And that's not all.
I found the digital signature from my bank, the reason why I was looking for it was that I'm prompted to "Always trust content from this publisher" every time I use my bank even though I accept it every time.
With Oracle java it just works and you only have to accept once.
I have a bug filed about it here [bug #941031]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/941031")
You can add yourself to the bug or comment it if you also are affected.
Added a screenshot of my digital signature provider in javaws.

Ah, glad you found it, this panel is new to me. I'm gonna check out the bug report. Thanks for taking the time to report it. 

<rant>I'm in a bad situation regarding access to my banks. 2 of them demand sun/oracle java 6 - Their IT is outsourced to the same company, so same security technology. They simply refuse any alternative. And the most important one, which I have to keep connected to all day for my business now demands clients to install an exe file and only work with Internet Explorer 8... Accessing via other IR version, browsers, OS or devices only lets you access a  limited number of features - you can't really make any transaction. It's ridiculous. It got to a point I had to create a VM for banking. Not to mention you already have to use the RSA token device, you have to pay and install the digital certificate from verisign, and, to make it a little more complicated, they eventually SMS you a code that you are asked in their interface after all these security stuff.  </rant>


Regards,
Effenberg

---

### Post by prana on 2012-02-25
> **effenberg0x0 said:**
> Ah, glad you found it, this panel is new to me. I'm gonna check out the bug report. Thanks for taking the time to report it. 

<rant>I'm in a bad situation regarding access to my banks. 2 of them demand sun/oracle java 6 - Their IT is outsourced to the same company, so same security technology. They simply refuse any alternative. And the most important one, which I have to keep connected to all day for my business now demands clients to install an exe file and only work with Internet Explorer 8... Accessing via other IR version, browsers, OS or devices only lets you access a  limited number of features - you can't really make any transaction. It's ridiculous. It got to a point I had to create a VM for banking. Not to mention you already have to use the RSA token device, you have to pay and install the digital certificate from verisign, and, to make it a little more complicated, they eventually SMS you a code that you are asked in their interface after all these security stuff.  </rant>


Regards,
Effenberg

OT: Yeah, I know that feeling. I think security is essential but it should get out of the way of a pleasant experience. My bank uses multi-factor auth using a combination of username/password, questions and images. I find it acceptable since a) the security level is higher, b) I can use an application like LastPass to get through each level of security and c) I can do online banking through any browser and OS.

---

### Post by Stinger on 2012-02-25
Yeah I know webbanking can be a pain in the ... :-\"
I tried the SMS-part too.
But I had everything working with icedtea and openjdk in oneiric, so it should be possible in precise too.
It seems like icedtea/openjdk might have been i386 and changed to amd64 at some point causing this mess ?

The only thing icedtea/openjdk is giving me now is quite a headache ](*,)

---

### Post by effenberg0x0 on 2012-02-25
> **Stinger said:**
> Yeah I know webbanking can be a pain in the ... :-\"
I tried the SMS-part too.


I tried talking to my bank support about Linux, Ubuntu, Java, IcedTea, OpenJDK, Digital Certificates that can't be exported from their proprietary software and properly imported at any OS/Browser, etc. The dude on the other side of the line probably had a good laugh at me while he put me on hold for half an hour :)

> **Stinger said:**
> 
But I had everything working with icedtea and openjdk in oneiric, so it should be possible in precise too.
It seems like icedtea/openjdk might have been i386 and changed to amd64 at some point causing this mess ?

The only thing icedtea/openjdk is giving me now is quite a headache ](*,)
I'm not confident that could be the cause... If you have half an hour to spend on this, I'd try installing VirtualBox and then install Oneiric on it. If you manage to use your bank in the Oneiric VM using IcedTea/OpenJDK, we'd be certain this is Precise related. I can't think of other way to test it.

Actually, before that, there's something else you can try. You probably have icedtea-7 installed, and you could try installing icedtea-6. That would go like:
```

sudo apt-get remove --purge icedtea-7-jre-cacao icedtea-7-jre-jamvm icedtea-7-plugin
sudo apt-get remove --purge openjdk-7-dbg openjdk-7-jdk openjdk-7-jre-lib openjdk-7-demo openjdk-7-jre openjdk-7-jre-zero openjdk-7-doc openjdk-7-jre-headless openjdk-7-source
sudo apt-get install --reinstall openjdk-6-dbg openjdk-6-jdk openjdk-6-jre-lib openjdk-6-demo openjdk-6-jre openjdk-6-jre-zero openjdk-6-doc openjdk-6-jre-headless openjdk-6-source
sudo apt-get install --reinstall icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-6-plugin 
```Just an attempt but, who knows, maybe it works. And, as a lost resort, you can always get sun/oracle java from Oracle website.

Regards,
Effenberg

---

### Post by Stinger on 2012-02-25
> **effenberg0x0 said:**
> 
I'm not confident that could be the cause... If you have half an hour to spend on this, I'd try installing VirtualBox and then install Oneiric on it. If you manage to use your bank in the Oneiric VM using IcedTea/OpenJDK, we'd be certain this is Precise related. I can't think of other way to test it.


There just might be another way, I have onieric on a usb-stick, could test with that instead.
I tried removing anything openjdk-7 related without any improvement.
the strange thing is that _the digtal signature from my bank is present_ (you can se it in my screenshot earlier on this thread) but openjdk don't seem to recognize it, and asks for approval every time I load my bank.
I use google-chrome but have tried firefox also, firefox is even worse, it just crashes when i click the run-button to approve the signature.
With Oracle java both browsers work flawlessly and only asks for approval the first time I run my webbank.

Will try with oneiric and your other suggestion and report back tomorrow (it's way past my bedtime here in denmark :) )
Thanks.

---

### Post by Stinger on 2012-02-26
Hi
I'm posting this from my live oneiric usb-stick.
I have installed icedtea/openjdk and its working perfectly, well allmost, "IcedTea Java 6 Web Start" wont start from /usr/share/applications, but my webbank is working fine, only have to approve the signature once.

I have made a couple of screenshots too.
"IcedTea Java 6 Web Start" is not present in system setting here either, I think this is a bug too.

---

### Post by effenberg0x0 on 2012-02-26
Another hypothesis: 

**1)** Maybe the PP install is missing a link to the IcedTea plugin, so the browser can use it properly?
```
cd /usr/lib/mozilla/plugins

```Check if there's a link there to the IcedTeaPlugin.so named libjavaplugin.so, and if this softlink is pointing to a valid location/file. If not, you'll have to fix it. Remove the broken link if any and create a new one with something like:
```
sudo ln -s /usr/lib/jvm/icedtea/jdk/jre/lib/IcedTeaPlugin.so libjavaplugin.so

```Just make sure IcedTeaPlugin.so is at /usr/lib/jvm/icedtea/jdk/jre/lib/. I don't have it installed right now to check it before creating the link. Use something like find or mlocate to adjust the path in the ln command. Then restart firefox and try again.

**2)** I have no idea where Java applets and stuff downloaded from websites is stored in IcedTea. Could it be that it is storing somewhere with wrong folder/file ownership and permissions? I have Googled a little and verified it should save stuff to the user home at ~/.icedtea. Maybe, just to make sure there's no ownership/permission problems, you could try something like:
```

cd
sudo chown $USER:$USER ~/.icedtea -R
sudo chmod 775 ~/.icedtea
sudo chmod 750 ~/.icedtea/security
sudo chmod 600 ~/icedtea/security/* -R

```

Regards,
Effenberg

---

### Post by larrypg on 2012-02-26
Hello,

Not sure our banks are set up the same way but at least with the one I have it works fine with 12.04 in Virtualbox. Just have to allow it with noscript.  If you need me to check further into it let me know.

---

### Post by Stinger on 2012-02-27
Thanks effenberg.

in ```
/usr/lib/mozilla/plugins
``` I have have symlink ```
libjavaplugin.so
``` which is pointing at 
```
/etc/alternatives/mozilla-javaplugin.so
``` that's another symlink which is pointing at 
```
/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so
```
So far so good.
I'm willing to try your suggestion regarding the permission to files and folders too, but I don't think that's the problem.
When I run 'javaws -wiever' from terminal as user I'm able to see the digital signature from my bank and so should the browsers be too.
BTW it's located in ```
~/.icedtea/security/trusted.certs
```
If I move or delete this file I'm not able to se my digital signature in 'jawaws -viewer' anymore. 

Do you know a way I can trace openjdk/icedtea to see if it uses, or tries to use, my signature file ?

I'll try to boot my oneiric-usb again later and see how links and permissions look there.

---

### Post by Stinger on 2012-02-27
larrypg,
thanks for offering to help, but I think your bank uses a different security mechanism.

Quick Update on Firefox-crash ! After today's updates Firefox does not crash anymore when I click the run-button to approve the signature :), it still asks for approval every time though :(.

---

### Post by zika on 2012-02-27
> **Stinger said:**
> Thanks effenberg.

in ```
/usr/lib/mozilla/plugins
``` I have have symlink ```
libjavaplugin.so
``` which is pointing at 
```
/etc/alternatives/mozilla-javaplugin.so
``` that's another symlink which is pointing at 
```
/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so
```So far so good.
I'm willing to try your suggestion regarding the permission to files and folders too, but I don't think that's the problem.
When I run 'javaws -wiever' from terminal as user I'm able to see the digital signature from my bank and so should the browsers be too.
BTW it's located in ```
~/.icedtea/security/trusted.certs
```If I move or delete this file I'm not able to se my digital signature in 'jawaws -viewer' anymore. 

Do you know a way I can trace openjdk/icedtea to see if it uses, or tries to use, my signature file ?

I'll try to boot my oneiric-usb again later and see how links and permissions look there.Check with update-alternatives (it looks that it is done that way)...

---

### Post by Stinger on 2012-02-27
Thanks zika
I tried ```
update-alternatives --list mozilla-javaplugin.so
``` from terminal and got ```
/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so
```, that seems ok, but I do not think there is any problems with the symlinks ? I think it's more about openjdk not seeing or recognizing my digital signature as it did in oneiric

---

### Post by Stinger on 2012-02-27
I found a way I can trace openjdk/icedtea to see if it uses, or tries to use, my signature file.

Open a terminal and type ```
export ICEDTEAPLUGIN_DEBUG=true
```, hit enter, now type ```
firefox
``` and enter, to launch the browser.
Browse to your webbank and try to login, wait for security approval.
Copy the info from your terminal, make a huge jar of coffee and spend the rest of the night trying to figure out what went wrong where :biggrin:
There is a lot of info but I don't know where to look for the clues ?

---

### Post by zika on 2012-02-28
Do You have proper entry for javaws in update-alternatives?

---

### Post by Stinger on 2012-02-28
using ```
update-alternatives --get-selections
``` from a terminal gives me ```
javaws                         auto     /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/javaws
```

---

### Post by Stinger on 2012-03-03
Ok good news !
Todays update to the icedtea and openjdk packages solved my problem.

As far as I know the problem was related to Icedtea. 

My digital signature is recognized now and I'm not asked for approval any more.

Works with both Firefox and google-chrome.

---

