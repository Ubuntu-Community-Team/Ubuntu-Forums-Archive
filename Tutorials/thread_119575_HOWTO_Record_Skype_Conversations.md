---
title: "HOWTO: Record Skype Conversations"
date: 2006-01-19
forum: Tutorials
---

### Post by majikstreet on 2006-01-19
Yes, it's possible. You've always wanted to. And now I can show you how.

Record conversations with skype! into mp3's!

It's amazing!

```

sudo apt-get install vsound sox sox-dev lame build-essential

```
Ok. We now have installed lame for mp3 encoding, and vsound, sox, and sox-dev for the program's dependancies. We have also installed build-essential, which will supply all the programs needed to compile programs. Cool, eh?

```

cd
wget http://www.twistedlittlegnome.com/skype-rec-kraken.tar
tar xvf skype-rec-kraken.tar

```

Now we have downloaded the program and untarred it.

```

cd skype-rec-kraken
make

```
Now, we have "made" the program. 

```

gedit skype-rec

```
Now we are editing the program. Scroll down until you see "my $SKYPEREC" edit the value to something like this: /home/yourusernamehere/skype-rec-kraken/libskype-rec.so

(you may have to change that, depending where you installed the program!)

If you run skype using a command other than "skype" edit my $SKYPE to the command you use to start up skype.

```

./skype-rec

```
That will run the program, and open up skype (make sure to close down skype before using this). You call your person, then you can hang up with them, and close skype. Then, the program will convert the file to mp3. 

The .mp3 file will be in the folder you installed the program to. (In my case, it was "/home/majikstreet/skype-rec-kraken/XXXXXXXX.mp3".. The name will appear odd, lol. You may want to edit the name lol.

Hope this works for you!

majikstreet

edit: posted in wiki: [https://wiki.ubuntu.com/SkypeRecordingHowto](https://wiki.ubuntu.com/SkypeRecordingHowto)

---

### Post by majikstreet on 2006-01-27
I don't think many people had a chance to see this, so I am bumping it...

I also want to add that there are some other files in the folder ending with .au (I believe)... you can delete those if you want.

thanks,
majikstreet

---

### Post by Evoreth on 2006-01-28
Yaay~!!
Thank you very much!

---

### Post by majikstreet on 2006-01-28
You're so welcome :P

---

### Post by Zhukov on 2006-01-30
Thanks a lot!!!

---

### Post by majikstreet on 2006-01-30
[QUOTE=Zhukov]Thanks a lot!!![/QUOTE]
Glad you like it :)

---

### Post by dickwall on 2006-02-24
Hi

I can't tell you how long I have been looking for a way to do this in skype, however I have noticed a slight problem. While the recording sounds magnificent, I co-host a podcast where all participants record their own mic feeds, and I use skype-rec for this now. I have noticed that my recordings come out of sync with the other conversations recorded on other machines, it is not a lot, but maybe 1 second is lost every 2 minutes, and the loss is pretty constant, so gradually my mic feed moves further and further ahead of theirs until things are really out of sync.

I am wondering what could be causing this - is it perhaps the sampling rate being 48000 Hz, or is it (as I more likely suspect) that some samples are being lost by the vsound redirect because the machine is busy doing other things. Assuming it is the sample rate, how can I force this to 44100 Hz, or if it is that some samples are being dropped, how should that be handled?

Hope someone can help, otherwise I am back to windows again for the recording :-(.

Thanks

Dick

---

### Post by Jonathan Métillon on 2007-05-04
> **majikstreet said:**
> That will run the program, and open up skype (make sure to close down skype before using this). You call your person, then you can hang up with them, and close skype. Then, the program will convert the file to mp3.

Thank you Majikstreet!

I did every step you said but after hanging up and closing Skype, it said:

```
No conversations to convert
```

Argh! I've lost a very important conversation here :(

What happened??

---

### Post by haelen on 2007-05-06
> **majikstreet said:**
> 

```

cd
wget http://www.twistedlittlegnome.com/skype-rec-kraken.tar
tar xvf skype-rec-kraken.tar

```


The file seems to have been moved (I got a 404)

Best,
Tim

OOps. Just found the new gz file via the wiki entry!

---

### Post by Jonathan Métillon on 2007-05-06
Yep Tim. I found it with Google, looking for "skype-rec-kraken.tar".

---

### Post by LegoAddict on 2007-05-12
> **Jonathan Métillon said:**
> Thank you Majikstreet!

I did every step you said but after hanging up and closing Skype, it said:

```
No conversations to convert
```

Argh! I've lost a very important conversation here :(

What happened??

*bump*

I have this problem too.

I did everything that you said, no hiccups.  I've checked it a bunch of times, it's fine.

I tested it with the test person, and I hung up and closed Skype, then Terminal said there had been no recorded conversations.  So I thought "fine... test must just not count or something".  So I talked with my producer (on a podcast) and tried to record it...

Didn't pick that up, and I'm sure my producer isn't automated.


Not important it didn't pick up that conversation, but I need something like this for an interview I need to do soon.


Help?

---

### Post by aparigraha on 2007-06-07
Another version of teh script is available. Now with OGG support.
Had the same sound issue but, changing Sound Configuration in Skype from ALSA to OSS did the trick.
It seems the path to /dev/dsp is needed.
Check out more at the skype forum:
[http://forum.skype.com/index.php?showtopic=19094]("http://forum.skype.com/index.php?showtopic=19094")
or download the upgraded version:
[http://sourceforge.net/project/showfiles.php?group_id=146056&package_id=160795&release_id=358917]("http://sourceforge.net/project/showfiles.php?group_id=146056&package_id=160795&release_id=358917")

---

### Post by flawedprefect on 2007-06-08
> **majikstreet said:**
> I don't think many people had a chance to see this, so I am bumping it...

I also want to add that there are some other files in the folder ending with .au (I believe)... you can delete those if you want.

thanks,
majikstreet

Dude - these files are actually EACH SIDE OF THE CONVERSATION as separate streams. AWESOME. I have been trying to kick the windows habit for ages cos I do a podcast about Heroes with two other people across the globe (one in Vienna and one in America). I have always opened up a recording program alongside skype. Of course this in Linux is pretty much impossible because if SKype uses ALSA, audacity freaks out, and sound recorder won't even open. This has solved this problem as well as another one: they always had to push their files over skype to me after the recording. Now I have each stream RIGHT THERE on my machine so cuts out download time.

This is one more reason to fully kick windows to the poverbial kerb. Oh it is teetering on the edge. TEETERING!

---

### Post by flawedprefect on 2007-06-19
Just upgraded to skype 1.4... this skype-rec doesn't seem to work with this version, because this one does not use OSS. Is there a version that does not require OSS? Have looked uo using a-oss... but I am afraid I don't know what I am doing there...

---

### Post by lduperval on 2007-06-29
I'm also interested in this. Also, is the skype-rec on sourceforge the same kraken version mentioned in this thread?

L

---

### Post by nike984 on 2007-07-18
> **Anic said:**
> Try [skypecap]("http://www.skypecap.com/"), its very good prog for skype!

It's a window app.
We need "Linux" app, not "window"'s.

---

### Post by flawedprefect on 2007-07-27
Fellas, I found this brilliant tutorial that worked for me:

[http://porpoisehead.net/hi/?q=node/23](http://porpoisehead.net/hi/?q=node/23)

It outlines how you can use the GNOME recorder (or even the KRecorder) within Linux Ubuntu itself, and by simply adjusting your Alsamixer settings, you can record the incoming signal to skype.

Give it a shot. You will find that once it works, all you have to tweak is the discrepancy in levels between the skype signal and your own input.

---

### Post by devi on 2007-10-01
This isn't working for me. I get no recordings in the directory. It's totally empty. :(

Tips/ideas? I'm using Skype 1.4

---

### Post by human-ness on 2007-10-16
> **Jonathan Métillon said:**
> Thank you Majikstreet!

I did every step you said but after hanging up and closing Skype, it said:

```
No conversations to convert
```

Argh! I've lost a very important conversation here :(

What happened??

I'm getting the same thing here Jonathan.  I followed the instructions down to the letter, but every time I quit Skype, it says "No conversations to convert" ...  Perhaps it's because the versions of Skype have changed.  I'm not sure.

Did anybody get the same thing, and if so, did you happen to find a solution to this problem?

Thank You in advance.

---

### Post by Scimu on 2007-11-01
Nice thanks.. Ill give it a try later.

---

### Post by haelen on 2007-11-02
The soxmix binary seems to be missing in Gutsy. skype-rec throws up an error.
It's not in the repository either (soxmix)

Anyone else encountered this?

Tim

---

### Post by ruisselet on 2007-11-05
Yes, in gutsy skype-rec won't start because soxmix has been removed. It can be replaced by 'sox -m'. I edited skype-rec like that (also removing the startup check for the soxmix binary), it does start up and record correctly.

There is a bug after a conversation is finished, so the temporary files remain, but at least they are saved. As far as I can see the bug is [https://bugs.launchpad.net/ubuntu/+source/sox/+bug/116470/](https://bugs.launchpad.net/ubuntu/+source/sox/+bug/116470/)

---

### Post by haelen on 2007-11-06
> **ruisselet said:**
> Yes, in gutsy skype-rec won't start because soxmix has been removed. It can be replaced by 'sox -m'. I edited skype-rec like that (also removing the startup check for the soxmix binary), it does start up and record correctly.]

Hi,

Thanks for the above. I'm pretty useless when it comes to editing code etc. Could you possibly paste an example of what you mean / did ?

Best,
Tim

---

### Post by DirtDart on 2007-11-07
Not to dampen anyone's attempt at this, but if you are in the U.S., you may want to check the laws of the state you are in before recording any phone conversation.

[http://www.rcfp.org/taping/]("http://www.rcfp.org/taping/")has a pretty decent discussion of what can/can't be recorded, and includes a list of all 50 states (the list is pretty useless if you're outside the U.S.)

---

### Post by ruisselet on 2007-11-11
> **haelen said:**
> Hi,

Thanks for the above. I'm pretty useless when it comes to editing code etc. Could you possibly paste an example of what you mean / did ?

Best,
Tim

Here is in attachment the modified skype-rec which uses sox -m instead of soxmix, which disappeared from sox version 13. (the file is actually skype-rec.txt to make the forum upload system happy, you will probably want to rename it and make it executable).

By the way, is there an "official" maintainer and location for skype-rec? This kind of change should be incorporated...

With sox 13 there is a crash doing the conversion, it has been marked as fixed in sox 14 changelog. Therefore I installed sox and libsox-fmt-all from hardy, it seems to work well on gutsy.

I also had to change a -v 1 option into vol 1.

Enjoy!

---

### Post by haelen on 2007-11-12
Hi,

I tried this using the Skype Test call. a) I couldn't hear myself in the playback and b) skype-rec didn't produce a file.

What's worse I now cannot make conference calls of any sort. :mad: Here's the error I got when I tested:


[IMG]http://www.timrowe.co.uk/images/audio.png[/IMG]

---

### Post by haelen on 2007-11-13
The above problem cleared upon powering off and on again. This time skype-rec seems to run ok - apart from the fact that it doesn't produce an actual recording!

Best,
Tim

---

### Post by amcvega on 2007-12-06
> **flawedprefect said:**
> Fellas, I found this brilliant tutorial that worked for me:

[http://porpoisehead.net/hi/?q=node/23](http://porpoisehead.net/hi/?q=node/23)

It outlines how you can use the GNOME recorder (or even the KRecorder) within Linux Ubuntu itself, and by simply adjusting your Alsamixer settings, you can record the incoming signal to skype.

Give it a shot. You will find that once it works, all you have to tweak is the discrepancy in levels between the skype signal and your own input.

 I couldn't get skype-rec  to work with Gutsy, Skype 1.4 so I tried this setup and it actually works!   Took me just 2 minutes to setup.  

Thanks for the hot tip!

---

### Post by motin on 2008-01-01
Same here. It is really nice to have a common way to record ANY program, not only Skype, and without relying on a script that gets out of date between skype updates. 

Make sure your mic sound is audible in the speakers and then record from "Capture" instead of "Microphone"is the trick. 

Works on Windows as well ;)

---

### Post by tmhai on 2008-01-10
I cannot get this to work. Skype runs, the terminal sits there saying "Starting skype..." and nothing occurs when I make calls. I get no mp3 files, no error messages, nothing.

Apart from the fact this script was written years ago, would someone be interested in updating it so it works with the latest version of Skype. I'm running Skype 2.0 Beta.

Else, would someone be interested in directing me to something that works.

---

### Post by tmhai on 2008-01-10
OK, I did the following and it gave me something to work with.

I downloaded the most up-to-date version of the skype-rec script at [http://sourceforge.net/projects/skype-rec/](http://sourceforge.net/projects/skype-rec/)

I unzipped the downloaded file and moved it to my /home/username/ directory.

I then opened the terminal and entered: cd /home/username/skype-rec

I then entered *make*. That worked well. I then entered *make install* and I got the following:
```
install -m 755 libskype-rec.so /usr/lib
install: cannot remove `/usr/lib/libskype-rec.so': Permission denied
make: *** [install] Error 1
```

So I entered *su root*, entered the root password, and tried the command again. That worked.

Next, I exited root, and edited the skype-rec.rc file. The thing I changed in that file was the location of the soxmix binary, which from what someone said in this thread, I changed to sox-m.

So, back to the terminal. I go to run skype-rec and I receive this error:
```
Can't locate /home/bobby/.skype-rec in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./skype-rec line 32.
```

Now that I have an error, perhaps someone could work with it. Also, in my Synaptics Package Manager, I couldn't find sox-m, but I could find sox package (which was already installed). And, yes, I ran* sudo apt-get install vsound sox sox-dev lame build-essential*.

---

### Post by HautingLu on 2008-02-18
> **tmhai said:**
> OK, I did the following and it gave me something to work with.

I downloaded the most up-to-date version of the skype-rec script at [http://sourceforge.net/projects/skype-rec/](http://sourceforge.net/projects/skype-rec/)

I unzipped the downloaded file and moved it to my /home/username/ directory.

I then opened the terminal and entered: cd /home/username/skype-rec

I then entered *make*. That worked well. I then entered *make install* and I got the following:
```
install -m 755 libskype-rec.so /usr/lib
install: cannot remove `/usr/lib/libskype-rec.so': Permission denied
make: *** [install] Error 1
```

So I entered *su root*, entered the root password, and tried the command again. That worked.

Next, I exited root, and edited the skype-rec.rc file. The thing I changed in that file was the location of the soxmix binary, which from what someone said in this thread, I changed to sox-m.

So, back to the terminal. I go to run skype-rec and I receive this error:
```
Can't locate /home/bobby/.skype-rec in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./skype-rec line 32.
```

Now that I have an error, perhaps someone could work with it. Also, in my Synaptics Package Manager, I couldn't find sox-m, but I could find sox package (which was already installed). And, yes, I ran* sudo apt-get install vsound sox sox-dev lame build-essential*.

I got the some error as you about can't locate /home....
I then copied skype-rec.rc to $HOME/.skype-rec/

And the error I get now is Directory /home/user/.skype-rec not allowed in require at ./skype-rec line 32.

Any ideas?

---

### Post by tareko on 2008-03-08
Hi all!

I have been helping a friend get Skype recording working on a Gutsy 7.10 system.  I have updated the [wiki page]("https://help.ubuntu.com/community/SkypeRecordingHowto") with instructions.

I also noted a small problem with the skype-rec file, and so submit here another slightly modified copy that does not create the same SOX crash.

tarek : )

---

### Post by [Neurotic] on 2008-03-12
> **tareko said:**
> Hi all!

I have been helping a friend get Skype recording working on a Gutsy 7.10 system.  I have updated the [wiki page]("https://help.ubuntu.com/community/SkypeRecordingHowto") with instructions.

I also noted a small problem with the skype-rec file, and so submit here another slightly modified copy that does not create the same SOX crash.

tarek : )

I just tried this on Hardy, and with Skype 2.0 beta, and it runs with no errors... except there is never anything in my ~/skype-recordings/ folder

I updated the skype-rec executable in /usr/bin/ with your edited file (thanks!) that was much appreciated, but no go :(

Any help would be appreciated.

---

### Post by [Neurotic] on 2008-03-12
Looking at the code for skype-rec.c, it seems to be recording on /dev/dsp, but I am using a USB headset with skype to talk, which explains why there is no recording.

Anyone know what I will need to change this to, or how to find out what I need to change it to?

---

### Post by [Neurotic] on 2008-03-12
On closer inspection to the code in skype-rec.c

```

int ioctl(int fd, request_t request, ...)
{
    static int (*func_ioctl) (int, request_t, void *) = NULL;
    va_list args;
    void *argp;

    DPRINTF("ioctl::%d\n", fd);

    if (!func_ioctl)
        func_ioctl = (int (*)(int, request_t, void *))dlsym(REAL_LIBC, "ioctl");
    va_start(args, request);
    argp = va_arg(args, void *);
    va_end(args);

    DPRINTF("ioctl::%d - %d\n", fd, dsp_fd);


    if (fd != dsp_fd)
        return func_ioctl(fd, request, argp);

    /* Capture the ioctl() calls to /dev/dsp1. */
    dspctl(request, argp);

    return func_ioctl(dsp_fd, request, argp);
}   

```

dsp_fd is ALWAYS -1 (if it gets to it at all).

This means nothing gets recorded.

This may be an issue on Hardy, but I've hit about my limit on C / soundcard programming for today, so it seems there is a bug in the code for this version of Skype (2.0) or Hardy, I've no idea which.

---

### Post by 655 on 2008-04-01
What's the verdict on this?  

I tried installing the upgraded SOX14 components, downgraded to Skype v. 1.3, and used the revised skype-rec.rc, but no conversations are being recorded to the conversations directory.

The program ran and exited flawlessly without printing any errors to the terminal, in both Skype 1.3 and 2.0

---

### Post by [Neurotic] on 2008-04-01
I've ended up running Skype in an XP VM, because there was no way to get this done.

Maybe now with pulse audio, but I can't seem to get skype to run under that, and/or get a sound recorder that will support it.

---

### Post by pablo88 on 2008-05-07
Hi -

I just stumbled across this:

[http://callgraph.in/faq.php](http://callgraph.in/faq.php)

Fifth FAQ from the end is:

Q: Are Linux/MAC clients being planned?
A: Yes, we are working on it. If you would like to try out a preview release then write to us here. 

The more that ask to test out their beta release the fatser we'll get it. I think  :-)

---

### Post by zomer on 2008-06-03
skype-rec 
In the result 
Starting file conversion process... 
Running skype... 

```
RtApiOss: OSS playback device (/dev/dsp) is busy. 

RtApiOss: OSS playback device (/dev/dsp) is busy. 

RtApiOss: OSS playback device (/dev/dsp) is busy. 

2008-06-03 17:50:09: Converting conversation 
2008-06-03 17:50:09: Not mixing, /home/zomer/skype-recordings/remote-20080603175009.au appears to be empty 
2008-06-03 18:36:35: Converting conversation 
2008-06-03 18:36:35: Not mixing, /home/zomer/skype-recordings/remote-20080603183635.au appears to be empty 
2008-06-03 17:50:19: Converting conversation 
2008-06-03 17:50:19: Not mixing, /home/zomer/skype-recordings/remote-20080603175019.au appears to be empty 

Please wait while conversion process finishes...
```

Why instead of one mp3 file I have 20 file *.au?
I`m skype version (skype_static-2.0.0.68-oss). Device in skype **/ dev/dsp**

Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Micro-Star International Co., Ltd. Device 7388
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

---

### Post by sivaprasad86 on 2008-06-05
Directory /root/.skype-rec not allowed in require at ./skype-rec line 32


Pls Suggest me

---

### Post by Whoopie on 2008-06-05
Hi,

there's a new tool called "Skype Call Recorder". See [http://forum.skype.com/index.php?showtopic=138491](http://forum.skype.com/index.php?showtopic=138491)

Best regards,
Whoopie

---

### Post by EFobes on 2008-06-17
Thanks for the info. You helped a lot of people. 

But when I try this step 

> **majikstreet said:**
>  
```

cd
wget http://www.twistedlittlegnome.com/skype-rec-kraken.tar
tar xvf skype-rec-kraken.tar

```
 

edit: posted in wiki: [https://wiki.ubuntu.com/SkypeRecordingHowto](https://wiki.ubuntu.com/SkypeRecordingHowto)


I get this in terminal
```

edward@edward-desktop:~$ cd
edward@edward-desktop:~$ wget http://www.twistedlittlegnome.com/skype-rec-kraken.tar
--11:48:11--  http://www.twistedlittlegnome.com/skype-rec-kraken.tar
           => `skype-rec-kraken.tar'
Resolving www.twistedlittlegnome.com... 67.19.210.34
Connecting to www.twistedlittlegnome.com|67.19.210.34|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:48:11 ERROR 404: Not Found.



```


Any ideas?

Thx

Ed

---

### Post by Zburatorul on 2008-07-11
Just google for skype-rec-kraken.tar and then install it from one of those links.

On a related note, whenever I try running skype-rec I get
```

Running skype...
ERROR: ld.so: object '/usr/lib/libskype-rec.so' from LD_PRELOAD cannot be preloaded: ignored.
QIconvCodec::convertFromUnicode: using ASCII for conversion, iconv_open failed
QIconvCodec::convertToUnicode: using ASCII for conversion, iconv_open failed
No conversations to convert
```

That library is in fact at that exact location. 
Any ideas what the issue could be? 
Thanks.

---

### Post by lduperval on 2008-08-15
I used the skype call recorder and it worked great, even on AMD64!

L

---

### Post by quill3033 on 2008-08-17
Ok I did nothing like what is described here. 
I have Ubuntu 8.04.
I have skype 2.0.0.72 (Debian not medibuntu in this case). I just went to the volume control (the one that is on top panel by default) and unmuted the microphone. Then I went to Applications --> Sound&Video -->Sound Recorder and chose in dialogue box option that says "Record from input", Mix (Mix mono works too). In the dialogue box option "Record as" I chose "cd quality mp3" and bingo. I start recording before I even ring. Then I save the file wherever I like - it gives you that option like with any other file. This is sooo useful for companies that record your conversation as they do nowadays - you can also have your own copy of what was said and store it in your computer. That is just great! I love ubuntu!

---

### Post by EFobes on 2008-08-17
Great solution, Audacity works equally well. There is also  a program called Skype Call Recorder which is great because you can configure it to automatically start recording whenever you make/receive a call and then it will ask you if it is ok to continue.

---

### Post by Ubuntiac on 2009-01-15
Hi,

I just came across a really easy method that works perfectly for me.

Install the deb of Skype Call Recorder from [http://atdot.ch/scr/](http://atdot.ch/scr/)

Run it. Run Skype. Tell Skype that yes, it's OK, for skype call recorder to access the api.

It Call recorder just sits in the system tray and asks for each call if you want it recorded. Then it saves the file with the date and who you were talking to in the file name.

So easy!

---

### Post by TDFlanders on 2009-01-19
As of 8.10 (and probably in 9.04 alfa-3 too): 

root@thomas-laptop:/home/thomas# apt-get install vsound sox sox-dev lame build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vsound
root@thomas-laptop:/home/thomas# date
Mon Jan 19 14:20:44 GMT 2009
root@thomas-laptop:/home/thomas# lsb_release -rd ; uname -a ; apt-cache policy vsound skype
Description:	Ubuntu 8.10
Release:	8.10
Linux thomas-laptop 2.6.27-11-generic #1 SMP Thu Jan 15 11:03:58 UTC 2009 i686 GNU/Linux
skype:
  Installed: 2.0.0.72-1
  Candidate: 2.0.0.72-1
  Version table:
 *** 2.0.0.72-1 0
        100 /var/lib/dpkg/status
W: Unable to locate package vsound
root@thomas-laptop:/home/thomas# apt-cache search vsound
root@thomas-laptop:/home/thomas# 


I am trying out the last advices on this post. Thanks everyone!

---

### Post by TDFlanders on 2009-01-19
Oops .. trying manual download.

thomas@thomas-laptop:~$ apt-get source vsound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for vsound
thomas@thomas-laptop:~$ wget [http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz) | sudo dpkg -i skype-rec-1.0
[sudo] password for thomas: --2009-01-19 14:30:43--  [http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz)
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/skype-rec/skype-rec-1.0.tar.gz?download&failedmirror=superb-east.dl.sourceforge.net](http://prdownloads.sourceforge.net/skype-rec/skype-rec-1.0.tar.gz?download&failedmirror=superb-east.dl.sourceforge.net) [following]
--2009-01-19 14:30:44--  [http://prdownloads.sourceforge.net/skype-rec/skype-rec-1.0.tar.gz?download&failedmirror=superb-east.dl.sourceforge.net](http://prdownloads.sourceforge.net/skype-rec/skype-rec-1.0.tar.gz?download&failedmirror=superb-east.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz) [following]
--2009-01-19 14:30:44--  [http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz)
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/skype-rec/skype-rec-1.0.tar.gz?download&failedmirror=superb-east.dl.sourceforge.net](http://prdownloads.sourceforge.net/skype-rec/skype-rec-1.0.tar.gz?download&failedmirror=superb-east.dl.sourceforge.net) [following]
--2009-01-19 14:30:44--  [http://prdownloads.sourceforge.net/skype-rec/skype-rec-1.0.tar.gz?download&failedmirror=superb-east.dl.sourceforge.net](http://prdownloads.sourceforge.net/skype-rec/skype-rec-1.0.tar.gz?download&failedmirror=superb-east.dl.sourceforge.net)
Reusing existing connection to prdownloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://puzzle.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz](http://puzzle.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz) [following]
--2009-01-19 14:30:45--  [http://puzzle.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz](http://puzzle.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz)
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 

[1]+  Stopped                 wget [http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/skype-rec/skype-rec-1.0.tar.gz) | sudo dpkg -i skype-rec-1.0
thomas@thomas-laptop:~$

---

### Post by TDFlanders on 2009-01-19
Ok, that link was dead. I downloaded manually and did the make + make install + cp skype-rec.rc to ~/.skype-rec according to instructions. I get no errors but the program won't work, probably due to this:

root@thomas-laptop:/home/thomas/Desktop/skype-rec-1.0# skype-call-recorder
bash: skype-call-recorder: command not found
root@thomas-laptop:/home/thomas/Desktop/skype-rec-1.0# apt-get install soxmix oggenc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package soxmix
root@thomas-laptop:/home/thomas/Desktop/skype-rec-1.0# 
root@thomas-laptop:/home/thomas/Desktop/skype-rec-1.0# apt-get install oggencReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package oggenc
root@thomas-laptop:/home/thomas/Desktop/skype-rec-1.0# 

Any ideas? Anyone has it in their ppa's?

Thanks people,

Thomas

---

### Post by TDFlanders on 2009-01-19
Whoops!

No alsa, no skype-call-recorder!

:(

---

### Post by skyperec on 2009-02-11
> **TDFlanders said:**
> Whoops!

No alsa, no skype-call-recorder!

:(

Ok friends,
Do not despair...
After one night of tinkering around with compiling and installing
I found this excellent application which works like a charm
for recording skype conversations:

Skype Call Recorder
here: [http://atdot.ch/scr/](http://atdot.ch/scr/)

Just install the .deb package and you are all set. You won't even need to restart Skype. 

It's a beauty.

Thank you thank you thank you [email]jlh@gmx.ch[/email], all the gods bless you and may you live long, healthy and prosperous.


:)

skyperec


Just great.

Ok, I am off to hit the bunk... :)

---

### Post by msully725 on 2009-05-11
> **msurman said:**
> There is also a newer skype recorder for Linux here:

[http://atdot.ch/scr/](http://atdot.ch/scr/)

Just works and amazing integration into the desktop.

Another vote for Skype Call Recorder! 

I had an emergency situation where I needed a recorder for a Skype interview, ASAP. A little googling and I stumbled on this thread. 

SCR is exactly what I needed! Awesome tool.

---

### Post by pablo180 on 2010-05-25
> **msully725 said:**
> Another vote for Skype Call Recorder! 

I had an emergency situation where I needed a recorder for a Skype interview, ASAP. A little googling and I stumbled on this thread. 

SCR is exactly what I needed! Awesome tool.

Agreed. Tried recording calls on Windows but finding something decent and free, and that is easy to set up, was a minefield, but on Ubuntu Skype Call Recorder worked straight away, even with my USB Phone!

Great little App.

---

### Post by Ubuntiac on 2010-12-19
Have you tried recording video with TalkAide? I've heard quite a few people complain that Skype video recording (on any platform) never really works consistently.

---

### Post by kince on 2011-01-31
you can now record both audio and video from skpe using skype recorder. :guitar:

To install it open terminal and paste
sudo add-apt-repository ppa:dajhorn/skype-call-recorder
sudo apt-get update
sudo apt-get install skype-call-recorder

via | [www.multimediaboom.com]("http://ubuntuforums.org/sudo%20add-apt-repository%20ppa:dajhorn/skype-call-recorder%20sudo%20apt-get%20update%20sudo%20apt-get%20install%20skype-call-recorder")[]("http://ubuntuforums.org/sudo%20add-apt-repository%20ppa:dajhorn/skype-call-recorder%20sudo%20apt-get%20update%20sudo%20apt-get%20install%20skype-call-recorder")

---

### Post by Ubuntiac on 2011-02-26
Awesome!

Looking forward to trying this out. Doesn't seem to be a Natty package yet. How does the video look? What options do they give for saving? (Codecs, size etc)

---

### Post by freedomAboveAll on 2011-08-16
> **kince said:**
> you can now record both audio and video from skpe using skype recorder. :guitar:

To install it open terminal and paste
sudo add-apt-repository ppa:dajhorn/skype-call-recorder
sudo apt-get update
sudo apt-get install skype-call-recorder

via | [www.multimediaboom.com]("http://ubuntuforums.org/sudo%20add-apt-repository%20ppa:dajhorn/skype-call-recorder%20sudo%20apt-get%20update%20sudo%20apt-get%20install%20skype-call-recorder")[]("http://ubuntuforums.org/sudo%20add-apt-repository%20ppa:dajhorn/skype-call-recorder%20sudo%20apt-get%20update%20sudo%20apt-get%20install%20skype-call-recorder")

Thank you for posting this.  

We have successfully recorded audio portion of skype calls with this tool.  It is very useful for this purpose.   

I did not see options for recording video.

Note to others:    Once installed, just type 'skype-call-recorder' on terminal command line to start it. The app runs in the background, icon appears on tooltray.

---

### Post by Yozhik on 2011-10-20
This was, without a doubt, one of the most useful tools in the Ubuntu Toolbox.

... and then along came Ubuntu 11.10 and trashed it all. :(


Skype Call Recorder no longer works, and there is NOTHING comparable to replace it.
Please, please, please ... find a fix for this?

---

### Post by rajesh.kalapura on 2011-10-20
Thanks for the tutorial...Nice One....

---

### Post by stephenbbb on 2011-10-28
to: majikstreet

sorry to bother u
following instructions from 

[http://ubuntuforums.org/showthread.php?t=119575](http://ubuntuforums.org/showthread.php?t=119575)

scb@scb-Aspire-5250:~$ sudo apt-get install sox-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sox-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sox-dev' has no installation candidate

pls advise if there is a solution

---

