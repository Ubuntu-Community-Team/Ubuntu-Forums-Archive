---
title: "guitarx jack cannot run"
date: 2014-12-06
forum: Ubuntu Studio
---

### Post by flex567 on 2014-12-06
I installed guitrarx and right after I started it I get this error. How can I fix it? I have ubuntu 14.04

[IMG]http://i62.tinypic.com/yh4pt.png[/IMG]

I plugged the guitar in and the sound didn't come out of speakers.

>  			 				[INDENT] 					Does your microphone work with other applications; can you record sounds?
Can you hear output from the mic through your speakers?
Does your webcam work with other applications, eg cheese or guvcview? 				
[/INDENT] 			
  			   		


I have also Win 7 installed alongside Ubuntu and on Win7 I have skype installed and it works without a problem(sound and video).

> [INDENT]                     As mentioned previously, open Pulseaudio Volume Control, make a  test call, and check where the audio stream from Skype is going. If you  don't have PAVControl installed, install it from Software Centre.

You need to look in the input tab and make sure that is set to receive  input from whatever mic you are using. Check the playback option to make  sure that is set to go to the appropriate device (speakers or  headphones). 

Don't change anything in the Skype audio options. That is set correctly.  You just have the stream going to the wrong device. Once you have  sound, we can have a look at the video issue.

PS: Please attach large pics by using Go Advanced and the paperclip icon  rather than pasting them into the body of your post. Thanks. I have  edited your last post accordingly. :wink:                 
[/INDENT]
            
                         

I have Pulseaudio Volume Control installed and I made a test call and I couldn’t hear my voice in the test call. I tried all 3 ports: line in, rear microphone and front and none worked in a test call.

---

### Post by deadflowr on 2014-12-06
Did you install jack(d)?
[https://help.ubuntu.com/community/What%20is%20JACK](https://help.ubuntu.com/community/What%20is%20JACK)

And also, did you start jack?

---

### Post by flex567 on 2014-12-06
maybe it is already installed. how can I find out if it is already installed.

---

### Post by deadflowr on 2014-12-06
> **flex567 said:**
> maybe it is already installed. how can I find out if it is already installed.

I would search the software center for jack, anything with a green mark on it is installed.
Or run a quick apt-cache policy or dpkg -s or dpkg -l on jackd.
apt-cache policy is, to me, the easiest to understand as it clearly states if any package is installed or not.
(the dpkg do as well, but not nearly as cleanly)
```
apt-cache policy jackd
```
But even if jack were installed, you most likely need to configure and start it yourself.
But doing that is simple with a frontend like qtjackctl, but there are other's in the software center as well.

---

### Post by flex567 on 2014-12-07
```

apt-cache policy jackd

```

This is the message from the command
```

seba@seba-H81-D3:~$ apt-cache policy jackd
jackd:
  Installed: (none)
  Candidate: 5
  Version table:
     5 0
        500 http://si.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages


```

```

http://si.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages

```

I get 404. 



To me it looks like I don't have Jack installed, how can I install it?

---

### Post by Rob Sayer on 2014-12-07
If you really have trouble telling if you have jackd installed you should be using synaptic package manager.  If you don't have synaptic install it.  Hit the search button and type the name.  It'll tell you if it's there or not.

You can find synaptic in software center.  It's a lot better than software center (which I haven't used in so long I forget how it looks) IMHO.  I always use the terminal or synaptic.  While I'm all for terminal skills I think newbies should learn synaptic first if they don't know how to do installs.

BTW always update before you install.

---

### Post by flex567 on 2014-12-07
```

BTW always update before you install.

```

what should I update? 

What is the difference between Synaptic and Software Center?

---

### Post by MartyBuntu on 2014-12-07
As a guitar player myself, I would highly recommend to you that you consider Ubuntu Studio...either as your main install, or dual-booting with your current Ubuntu.

Jack is pre-installed, as well as many other music orientated utilities. Not to mention that Ubuntu Studio ships with a low-latency kernel, which is of some benefit when attempting audio production.


Give it a try.

---

### Post by flex567 on 2014-12-07
For now I would like to just install jack and try guitarx and after that I will see

---

### Post by deadflowr on 2014-12-07
> **flex567 said:**
> 
<snip>
```

http://si.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages

```

I get 404. 

I don't know what this means?
Elaborate on where this comes from, or what you were doing that it shows a 404.

> To me it looks like I don't have Jack installed, how can I install it?

You can get jack by installing one of the few graphical frontend interfaces, like qjackctl or  G jack transport, and then you can control how jack functions.
(You can control how jack functions well enough using command line but the gui frontends will probably be more easier for you.)

> **flex567 said:**
> ```

BTW always update before you install.

```

what should I update? 
You update the entire system.
I'd use the software updater, but you can run the command line comannds
```
sudo apt-get update
sudo apt-get upgrade
```

> What is the difference between Synaptic and Software Center?

The packages between the software center and synaptic are the same, but synaptic is more versatile and does not have the extra cruft the software center has which does not add to ease of installation of software; like the rotating graphical banner on the home page\ which adds to the unnecessary resource usage of the system.
Also the software center is not a full package manager like synaptic. Where as synaptic allows you do truly manage your packages, with relative ease. The software center is more about installation and removal of packages, and actual package management, like updating packages,is rather clunky.

Hope that helps.

---

### Post by flex567 on 2014-12-08
error 404 page cannot be found for this page: [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages

so how should I now install qjackctl ?

---

### Post by deadflowr on 2014-12-08
> **flex567 said:**
> error 404 page cannot be found for this page: [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages

so how should I now install qjackctl ?

Was that the only error?
What was the full output for sudo apt-get update

---

### Post by Elfy on 2014-12-08
> **flex567 said:**
> error 404 page cannot be found for this page: [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages

so how should I now install qjackctl ?

```
sudo apt-get install qjackctl 
```

IF you are getting errors from some mirrors - change the mirror. [https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

---

### Post by flex567 on 2014-12-08
now I get this error: 
[IMG]http://i59.tinypic.com/dr60n.png[/IMG]

---

### Post by deadflowr on 2014-12-08
Did you make your connections using the connect button?

---

### Post by flex567 on 2014-12-09
How can I connect, when I click connect new window opens with 3 tabs (audio,midi,alsa)?

---

### Post by Elfy on 2014-12-09
*Thread moved to **Ubuntu Studio**.*

---

### Post by deadflowr on 2014-12-09
> **flex567 said:**
> How can I connect, when I click connect new window opens with 3 tabs (audio,midi,alsa)?

Most likely in alsa you should see your actual devices and possibly a dropdown arrow.
It should have a split column/pane as well.
One pane should say something like inbound and the other outbound.
To make connections you "highlight" or click on the device name in inbound and then click on the device name in outbound.
When both are selected you should see the connect button will be enable.
When you click on the connect button a line will appear showing that the two devices are connected.
If you are unsure whether or not the connections are the right connections to use, or if more connections are available you can also connect those, as well as connect those to the existing connections, if that makes sense.
When they are set start jack.
And see what happens.

---

### Post by flex567 on 2014-12-09
I get this error
[IMG]http://i62.tinypic.com/25q8z9t.png[/IMG]

---

