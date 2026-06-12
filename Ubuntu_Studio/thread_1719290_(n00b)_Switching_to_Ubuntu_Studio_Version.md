---
title: "(n00b) Switching to Ubuntu Studio Version"
date: 2011-04-01
forum: Ubuntu Studio
---

### Post by JamesBartlett on 2011-04-01
Right, I recently, accidentally converted from Win7 to Ubuntu, and I while I quite like my new OS, it lacks certain things that I used a lot, namely music editing (I refused to pay for a mac), and I've stumbled across Ubuntu Studio Version, but what I'd like to know is what is it exactly? Whats the pros and cons compared to the standard(?) version, and Is it easy to switch and keep all my settings/progs/files? Thx!

---

### Post by beefheartvliet on 2011-04-01
If you use the synaptic package manager from inside your ordinary ubuntu installation, you can upgrade your existing installation to ubuntu studio. just type ubuntu studio in the seach. You might want to install everything. as this will include graphics and media packages too :-)

---

### Post by JamesBartlett on 2011-04-01
> **beefheartvliet said:**
> If you use the synaptic package manager from inside your ordinary ubuntu installation, you can upgrade your existing installation to ubuntu studio. just type ubuntu studio in the seach. You might want to install everything. as this will include graphics and media packages too :-)
So (sincere n00b aplogies) it will literally upgrade the OS keeping everything as it is?

---

### Post by beefheartvliet on 2011-04-02
I had no problems when I did it ;-) That's as fair as I can say. It goes without saying. You will always be better with a fresh installation. 
Have fun ;-)

---

### Post by riffey#4 on 2011-04-03
From one noob to the other:
I did it the other way around: I did a clean install of Ubuntu Studio, but I can install and use all the programs that come with regular Ubuntu. 
Hope this helps!

---

### Post by paulhart on 2011-04-03
James Bartlett, my thoughts... It is my understanding that you aren't changing the underlying OS, it is just a variant "flavor" of the user interface and programs. As others noted, it is easy, and if you select all of the possible programs in the Update Manager for Ubuntu Studio it will add a "ton" of programs for all kinds of media, graphics, audio, video, top flight stuff. It is the version of Ubuntu specifically tuned for creative types, just as there are other versions that are more suited for the scientific types. Anyway, I have been running it for a couple of versions, great software choices.
Paul

---

### Post by JamesBartlett on 2011-04-05
Right, I think I've upgraded with Synaptic. The boot screen shows Ubuntu Studio, and I do seem to have a load of new programs in the Sound & Video Section, but I can't run them! Some of them I get the splash screen, and others just don't appear to run, Other programs not associated to USV work (e.g. Firefox and RhythmBox) but not the USV programs!? I don't think its the hardware as the comp was bought for £500 from PC World only 6 months ago, and like I say everything else seems to work...

Is there an Ubuntu equivalent to the Task Manager feature found in Windows OS's?

---

### Post by Pablo_F on 2011-04-05
> Is there an Ubuntu equivalent to the Task Manager feature found in Windows OS's? 

Kind of. System -> Administration -> System Monitor 

htop is far better.

However, when a program misbehaves the best thing is launching it from a terminal to see the error messages. 

Of course, you need to know the exact command, which usually is the name of the program in lower case. Anyway, you can use this trick: Drag the icon from the menus to the desktop, right-click on the desktop icon and read the command in the properties window. 

On the other hand, it is very important that you know that, roughly summarizing, there are two audio systems or sound servers in ubuntu: pulseaudio and jack. Both use the alsa drivers but behave very differently. 

Pulseaudio is for desktop use. Jack is for music creation / pro-audio use. They can coexist, but, as a first approach, think of them as if they can't. See [http://0pointer.de/blog/projects/when-pa-and-when-not.html](http://0pointer.de/blog/projects/when-pa-and-when-not.html)

So, you need the jack server up and running to use tools like ardour, hydrogen, rosegarden, and more (the "jack-aware" or jack client apps). You will see a tool called Jack Control. It is used (between other things) to configure the jack server. This is essential. I suggest you take a look at jackaudio.org. 

By the way, in order to use jack in realtime mode (strongly recommended) it is very important that your user has rtrprio and memlock privileges. I write words so you can search the internet with them, if you don't mind. 

Also, note that some apps and tools included in ubuntustudio-audio are not very useful or up to date. You can always edit the menu.

Cheers, Pablo

---

### Post by JamesBartlett on 2011-04-05
Okay, Firstly, your help is GREATLY appreciated. Many heartfelt thanks.
Now, initially, most of what you said to me was alien, I am certainly very amateur, and new to both musical development, and the linux environment. I had a look at the things you showed me, and I browsed around online. I have never heard of JACK/Pro-Audio, but that site helped a good bit, I do understand the concept of API's. I had a look at Synaptic, and it appears I have JACK installed. I never specifically chose to, and don't know if this is a result of upgrading to USV. I did use Synaptic to download a couple of other things whcih sounded interesting and JACK-related, but to no avail in terms of running the programs.

However your mention of rtrprio and memlock threw me a bit. I Googled them both extensively (i'm assuming you meant rtprio - not trying to be picky, we're all victims of typos) and the information I found was very difficult to understand, and I'm not entirely sure where I stand.

I think I have JACK on my system, but I'm still a bit lost after that. From looking at what you showed me, I'm sure an explanation would require a Herculean effort on your part, but if you could point me in the right direction, I'd be immensely grateful. Rest assured, I really have searched a lot.

Many thanks Pablo, James

> **Pablo_F said:**
> Kind of. System -> Administration -> System Monitor 

htop is far better.

However, when a program misbehaves the best thing is launching it from a terminal to see the error messages. 

Of course, you need to know the exact command, which usually is the name of the program in lower case. Anyway, you can use this trick: Drag the icon from the menus to the desktop, right-click on the desktop icon and read the command in the properties window. 

On the other hand, it is very important that you know that, roughly summarizing, there are two audio systems or sound servers in ubuntu: pulseaudio and jack. Both use the alsa drivers but behave very differently. 

Pulseaudio is for desktop use. Jack is for music creation / pro-audio use. They can coexist, but, as a first approach, think of them as if they can't. See [http://0pointer.de/blog/projects/when-pa-and-when-not.html](http://0pointer.de/blog/projects/when-pa-and-when-not.html)

So, you need the jack server up and running to use tools like ardour, hydrogen, rosegarden, and more (the "jack-aware" or jack client apps). You will see a tool called Jack Control. It is used (between other things) to configure the jack server. This is essential. I suggest you take a look at jackaudio.org. 

By the way, in order to use jack in realtime mode (strongly recommended) it is very important that your user has rtrprio and memlock privileges. I write words so you can search the internet with them, if you don't mind. 

Also, note that some apps and tools included in ubuntustudio-audio are not very useful or up to date. You can always edit the menu.

Cheers, Pablo

---

### Post by Pablo_F on 2011-04-05
Hi James, 

No problem. Yes, I meant rtprio. 

I am a mere user so I could be a bit inaccurate in some terms. This stuff is very technical and beyond my knowledge.

However I see that GNU/Linux systems tend to be very safe by default and a user does not have certain privileges, like the ability to lock memory or run processes in realtime mode. (Here, the word "user" is used as "UNIX user". A computer can have more than one user, even if it is the same person who has two user accounts)

On the other hand, Jack, by nature, needs these privileges, so the user who runs jack must have them too. 

So, you just could run the jack server as administrator, with sudo, but this is not recommended.

To achieve it, there is a file called /etc/security/limits.conf (or any file inside the directory /etc/security/limits.d/) that sets those privileges for the users. Tipically, the privileges are set for a certain group. Then you have to make sure that the user who runs the jack server is a member of that group.

Recently, in Debian/Ubuntu, the "limits.conf" file is set semi-automatically (it needs manual confirmation) in */etc/security/limits.d/audio.conf* when you install the jackd package and it sets the rtprio and memlock privileges for the "audio" group, with two lines similar to:

@audio rtprio 99 
@audio memlock unlimited

Now, to complete the configuration, you have to make sure that you (the user who wants to run jackd) are a member of the "audio" group. See Users and Groups in the System menu. You can also do it in a terminal with:

sudo adduser your_user_name audio

If, when you installed jackd, you chose NO (the "safe" and useless option if you want a personal computer to make music), you have to revert this, either by manually editing the limits.conf file, or by running again the post installation script of jackd, with this command:

sudo dpkg-reconfigure -p high jackd

(it could be "jackd2" or "jackd1" instead of "jackd", depending on the ubuntu version and the jack version installed)


These changes in limits configuration and users/group need a computer reboot. To make sure that you have the said privileges, you can run the command:

ulimit -r -l

which should return, ninety-something and a good amount of RAM in kb, or unlimited. I think that there is no problem with unlimited in a personal computer.  In my case:

real-time priority              (-r) 99
max locked memory       (kbytes, -l) unlimited


Now, Jack Control is a graphical tool to configure and start the jack server (aka, the jack daemon or jackd). It can also be used to make connections between jack clients (the audio card and the jack-aware apps).

There are several tutorials on jack configuration (Jack Control, setup button) but note that it depends a lot on the hardware used, so don't take them too literally. If you have any problem or doubt show the contents of messages window of Jack Control (aka qjackctl).

Cheers, Pablo

---

### Post by cfhowlett on 2011-04-05
Greetings:

If I understand your initial question, you're seeking to do some music editing.  Technically you DO NOT need to install Ubuntu Studio as you can selectively install individual programs.  In your case, you probably want to take a good look at Audacity.  

Like you, I started with a vanilla installation of Ubuntu and then added the 1000 blade Swiss army knife aka Ubuntu Studio.  Most of this distro seems aimed at the linux musician, so you should feel quite confident that the tools you want are there somewhere. Personally, I have found it more than sufficient for podcasting.

Understand that Ubuntu Studio ADDS programs and functionality to your pre-existing default Ubuntu installation.  I suggested you start your music editing self-education with Audacity because it is better documented and more n00b friendly than Ardour.  However, among professional linux musicians, Ardour seems to be preferred as it is a full-fledged Digitial Audio Workstation rather than a music editor. 

Personally, I use UbuntuStudio and Audacity primarily for podcasting.  (Podcast sample: [http://kokujinchronicles.podomatic.com]("http://kokujinchronicles.podomatic.com")) However, I have also done a video combining Audacity and OpenShot assets.  (Video sample:  [http://www.youtube.com/watch?v=XDL6fMQXIoE]("http://www.youtube.com/watch?v=XDL6fMQXIoE")).  Hope this helps.

---

### Post by JamesBartlett on 2011-04-06
Thanks mate, it does, and I've subscribed to your podcast. :)

---

### Post by JamesBartlett on 2011-04-06
Right, this thread seems to be getting tied in with one I had initially started separately, and I DON'T want to be found guilty of double-posting. For the time being, I'll leave this as unsolved, because it is, but when the other thread is solved. I'll sort this one too.

Any further comments, questions, if you could please post them here:[http://ubuntuforums.org/showthread.php?t=1720403](http://ubuntuforums.org/showthread.php?t=1720403)

Thanks.[]("http://ubuntuforums.org/showthread.php?t=1720403")

---

### Post by cfhowlett on 2011-04-06
> **JamesBartlett said:**
> Thanks mate, it does, and I've subscribed to your podcast. :)

Well, then, that makes you my very first confirmed Ubuntu Studio subscriber.  Welcome!

---

