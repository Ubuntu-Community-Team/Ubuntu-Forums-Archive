---
title: "How to perform scheduled audio recordings"
date: 2010-09-08
forum: Ubuntu Studio
---

### Post by rmcellig on 2010-09-08
My understanding is that the only way I can record radio shows from my radio (which is plugged into my computer), is to use arecord with a crontab?

I am not trying to record streaming audio, but simply audio from my radio.

I was looking for a GUI solution if at all possible.

Where can I download arecord from? Is it a GUI tool or a command line tool?

I have a feeling that if I set up a crontab that will allow me to record radio shows at different times and dates that it would be pretty easy to maintain and modify. My output audio format would be aiff.

Since I am new to this way of doing this, I would really appreciate a detailed response as to what exactly I need to do.

---

### Post by Pablo_F on 2010-09-10
In gnome you can use [gnome-schedule]("http://gnome-schedule.sourceforge.net/").

sudo apt-get install gnome-schedule

Applications -> System Tools -> Scheduled tasks

Then, you need to know the right command. 

arecord is a rather "low level" tool and certainly not the only way you can capture audio. It is command line only, and rather involved. You probably have it already installed. Try "man arecord" in a terminal.

I am sure that pulseaudio (the default audio system in ubuntu) has a way to do this. I am sorry I can't help you with pulseaudio.

Because I use jack as my normal audio system, I use jack_capture which is a simple jack-aware audio recorder. 

So, if you manage to have jack up and running, jack_capture is the way to go. It has both GUI and command line. However, it does not encode to aiff on the fly, but you can do that afterwards, even as another scheduled task so you don't have to bother to do it manually each time. 

To sum up, first decide your audio system. If you don't want to bother with jack (you normally don't need it for "Desktop use"), I think "Multimedia and video" is a better place to ask than "Ubuntu Studio". If you want to go the jack way, just ask again. Jack_capture is not in the official repos. 

Cheers! Pablo

---

### Post by rmcellig on 2010-09-10
Thanks Pablo_F. I'm not too concerned about what format I capture the audio in because I can always convert it to m4a or mp3 format after.

The way I have it now on my Mac, I use Audio Hijack Pro (Jack_Capture for ubuntu)) which has a very easy GUI to understand. I use it to schedule my recordings. The shows are recorded in AIFF format. I use Sound Studio (Audacity in Ubuntu) on my Mac to edit and finally save the file in MP3 format.

I will check if I have Jack Capture and post back as to where we go from here.

I have gnome-schedule. What is a simple test that I can do with gnome-schedule to make sure it is working properly? Do I have to turn cron on first? How can I check if Cron is on?

Thanks again Pablo_F!!

PS: I'm not sure how to move this thread to the Multimedia section.

---

### Post by Pablo_F on 2010-09-10
Hi!

You don't have to move the thread, you can't, even, afaik. I just suggested the idea for further questions or so, because here most people are friends of jack and it could be overkilling to use the jack audio server just for recording audio. However, it is the only option I am familiar with so I will explain to you how I would do it in your case. 

Afaik, there is not a jack-aware audio recorder that can schedule recordings easily from a GUI, so you have to use two programs: The scheduler (easy, with a gui) and the recorder (not so easy. No gui and you don't need it because you will not be in front of your computer). 

So first of all, learn how to use gnome-schedule GUI. It is really easy. Try a couple of tests:

1) New --> "A task that launches one time". Description: test1. At (choose a time, one minute in the future for instance). Select "X Application". In the task field put the following: 
[B]
nautilus[/B]

This will launch nautilus, the gnome file browser. 

2) Now, try with a task that launches recurrently and the same command (again "nautilus", without quotes, in the command field). For a quick test, select "at every minute". Again, choose X aplication. Does it work? OK, delete it.

Now that you have learned how to schedule tasks, you need to know how to define the right task.

So, next step is getting jack up and running. This is the hard part. Jack configuration can be tricky. What audio card do you have?
Please give the terminal output of

**aplay -l**

And do a:

**sudo apt-get install qjacktl jackd**

jackd has a post inst configuration script. Choose YES (TAB key). Once finished the installation, add your user to the audio group:
[B]
sudo adduser your-username audio[/B]

Then, add a repo that has a recent version of jack_capture:

**sudo add-apt-repository ppa: philip5/extra** (no space between the colon and the p, please).

Update the software sources and install jack-capture:

**sudo apt-get update && sudo apt-get install jack-capture**

Now, go to system -> administration -> software origins and, in the "other software" tab, disable Philip's PPA.

Now, reboot the computer. 

Now, try to launch the jack server, through  Applications -> Sound and Video -> jack Control, Start button. 

Next step, tomorrow. . Tell us if jack starts (if you see "Started" in the display and no error messages). Otherwise, copy the content of the message window, And please, either way, give the aforementioned output of "aplay -l" command, so we can help better.

Cheers! Pablo

---

### Post by rmcellig on 2010-09-10
Thanks Pablo!! I will let you know how it goes!! Much appreciated beleive me!!

---

### Post by rmcellig on 2010-09-14
I ran into problems with the first code that you posted. Take a look at the screenshot. By the way, everything went fine with the scheduled tasks test.

It seems that I have Jack already installed. I checked under Sound and Video and I see Jack Control, Jack EQ, Jack Rack, and Jack Timemachine

---

### Post by Pablo_F on 2010-09-14
Hi,

Sorry, I wrote the package name wrongly. It should be "qjackctl". Anyway, you have already installed it (it is Jack Control in the Sound and Video menu). Remember that you can always use Synaptic (in System -> Administration) to install software packages. You can use the software center too. apt-get is quicker although less intuitive. 

You have to add your user to the audio group. If your user name is rmcellig, you should type:

**sudo adduser rmcellig audio**

Now, reboot the computer.

Launch Jack Control and start the server. I think the default setup will work. If it works, open the Connection window.

"System" is your audio card. If you want to listen to the radio trough the audio card and record it without problems, you should avoid hardware mixing. Then connect the system:capture port (or both of them if the input is stereo) to the first two system: playbacks and check the sound.

In a command line:

**alsamixer**

Use the following keys:
TAB  (to change playback, capture, all)
M (to mute/unmute a channel)
Cursors (to choose channels and increase / decrease levels)

You can also use gamix, gnome-alsamixer, qamix or other graphic ALSA mixers if you prefer. 

I cannot test your case because I don't have your card. But this step is crucial. If all goes well, the rest is very easy:

Boot the computer, connect the radio to the audio card, connect the system captures to the system playbacks, open a terminal and type this command:
[B]
jack_capture -mp3[/B]

This will encode on the fly to mp3 so you won't need to use an editor afterwards. The recorded audio will be located in your home folder with the default name, "jack_capture_01.mp3". By default, the second recording will not overwrite the first one but it will be named "jack_capture_02.mp3", and so on.

You can also specify a location and a name for the recorded audio. For example.

**jack_capture -mp3 /home/rmcellig/myaudiorecordings/myaudiofile.mp3**

But note that in this case a second recording will overwrite the first one. Of course, the directory "myaudiorecordings" or whatever you call it must exist.

A handy option for the scheduled recording might be the duration, "-d". Like this:

**jack_capture -mp3 -d 3600 /home/rmcellig/myaudiorecordings/myaudiofile.mp3**

or just:

**jack_capture -mp3 -d 3600**

if you prefer to rename afterwards.

This will record "what you are hearing through the speakers" for 1 hour (3600 seconds).

For a full list of options see:

**jack_capture --advanced-options**

Now, in the scheduler, you must add the ampersand to the selected command. For example:

**jack_capture -mp3 -d 3600 &**

If you don't want to use the duration option, but just want to stop it at another given time, use the following command to stop recording:

**killall jack_capture**

Although the duration option is a better idea, imo. 


If you are in front of your computer, you will prefer to use the jack_capture GUI. You should see it in the "Sound and Video" menu, I am rather sure, but if not, add a launcher with the following command:

**jack_capture_gui2**

Another useful simple jack-aware recorder is timemachine. This records the past. For example, you are listening to the radio, and you hear something interesting or you are playing the guitar with rakarrack and you play your best solo ever, press the record button and voilà, recorded. By default it travels 10 seconds back to the past, but you can change that. See 
[B]
timemachine --help[/B]

The drawback of timemachine is that you have to make the connections manually if you use its gui. 

On the contrary, in jack_capture the default behaviour is: "connect to the inputs every existing connection to the system playbacks", so literally, it records what you are hearing through the speakers


To sum up, listen to the radio through your computer with jack, not just through the sound card. Use jack_capture and don't forget the ampersand for the scheduled tasks.

Another trick: When you try listening to the recorded audio while jack is running you will hear nothing with the ubuntu's default audio players if you do nothing else. You can "jackify" them but you can also install Aqualung which is a jack-friendly audio player. Or you can use audacious with the jack output plugin.

Happy recording and sorry for the long post.

Pablo

---

### Post by rmcellig on 2010-09-14
Thanks Pablo!! Is there a way to do all of this with the GUI instead of the command line? Just wondering.

---

### Post by Pablo_F on 2010-09-15
Hi!

The command line is easier for me to write down the instructions :)

**To access the hardware mixer of your sound card to avoid internal mixing** (so you eventually can route the signals between the card and applications -e.g. jack_capture- via jack):

System -> Administration -> Synaptic: Search: "gamix" (without the quotes). Install it (mouse, right click).

Applications -> Sound and Video -> ALSA mixer

**To record with jack_capture while you are in front of your computer:**

Applications -> Sound and Video -> Jack_capture

Change the default settings to mp3 or ogg so you don't need to compress the audio later. 

I don't know of any jack_aware audio recorder that can schedule recordings by means of its own gui, that's why I am suggesting the task scheduler + a command line recorder.

I just suggest, before scheduling the recording command, try it in a terminal.

Now, don't fear the terminal. You don't need to even type the commands. Use ALT + middle button to resize windows so you can see the web browser with this thread and a terminal window side by side. Then you can just drag text from the browser to the terminal. Or to the scheduler, once you are fine with the right command (again, in the scheduler add "&" to the command!). You can also "select and drop" with the mouse. You drop the text with the middle button. You don't even need the keyboard to copy-paste text in ubuntu. 

Cheers! Pablo

---

### Post by rmcellig on 2010-09-15
Thanks for all your help Pablo. I struggle quite a bit in the terminal. I use the terminal on occasion. I guess because I think that Linux is one of the best if not the best OS I have ever used, that there would be an application out there that would do scheduled recordings. There are a few on the PC side and some on the Mac side. I use Audio Hijack Pro on the Mac because I can record on the fly if something of interest comes on the radio. 

I host a radio show so I need something that is easy to use and setup. This is the only stumbling block I have come across in Linux that is preventing me from using this OS on a full time basis. If you google Audio Hijack Pro, you can go to their web site and see what I am using on the Mac side. I guess another alternative would be to download a PC app that would do this and try running it in WINE.Although, a Linux solution would be what I would really want.

The schedule task application is very easy to set up in Ubuntu. It's just all the Jack stuff and the configuring that is involved to get everything going that I find kind of intimidating.

I hope you know where I am coming from and I will try to follow your instructions just to see if I can get through it and learn something. Bottom line is that I need something that is easy, intuitive and fits the needs I described above. When you work for a radio station, time is so precious and you have to make the most of it when it comes to recording etc...

Thanks again Pablo!!

---

### Post by Pablo_F on 2010-09-16
Hi, 

The jack server is supposed to exist for music production. For desktop tasks it can be overkilling. 

However, there could be a pulseaudio-aware recorder that allows scheduling. I just don't know.

GNU/Linux is a great OS with few desktop users, so it is no wonder that it has fewer apps. In adition, few users mean mean less direct support. Forums are great but a knowledgeable neighbour is far better. 

In Linux you can do wonders but I agree that it has a steep learning curve for some tasks that nowadays are easier to get going in other platforms because their apps are not migrated to Linux.

Anyway, if you have the time, try the jack_capture thing. 

Enjoy! Pablo

---

### Post by seventyeights on 2010-10-04
Hi.

I record "red eye radio" every night from 1 to 5 am with rock-solid reliability. I hope I can help and make for you scheduled radio recording so easy a caveman could do it.

**1)** First, make sure you have lame:

**sudo apt-get install -y lame**

**2)** Now to make a bash script. Open gedit and copy one of the lines below into it. Save it with the filename **record-the-radio.sh**

(for AM or mono recording)
```
arecord -f S16_LE -c1 -r22050 -d 14400 -t raw | lame -r -s 22.05 -m m -b 64 - Red_Eye_Radio_$(date +%F).mp3
```

(for FM or stereo recording)
```
arecord -f S16_LE -c2 -r44100 -d 14400 -t raw | lame -r --preset medium - Red_Eye_Radio_$(date +%F).mp3
```

Note: The -d 14400 is the duration of the show in # of seconds.  (4 hours * 3600 seconds)

Note: "$(date +%F)" inserts the current date into the filename. "man date" for more info.

**3)** Give your script permission to run.

**chmod +x record-the-radio.sh**

**4)** Now to adjust your audio input levels. Turn on your tuner, make sure it's plugged in to the right jack. 

Start recording by executing the bash script:

**./record-the-radio.sh**

You may or may not hear what is being recorded. It doesn't matter for it to work. (if you must have a monitor, then search "alsa loopback" for help) 

Go to System/Preferences/Sound and click on the input tab. Set the level so that the meter averages 70-80%. Mine is set to the "unamplified" notch for a line-level source. 

Stop the recording by typing ctrl-c in the terminal and play it in your favorite player to make sure it sounds ok. Compare the volume level with an mp3 from your cd library. If the sound is muffled, then the input level or volume on the radio is too high (are you using the earphone jack on a transistor radio?)

**5)** Now set up your crontab. Mine is set to execute the recording script at the 1st hour of each day. For more info, search crontab.

**crontab -e**
(if you are asked to choose an editor, choose 2 for nano)


You should now see
```
# m h  dom mon dow   command

```

on the third line, enter

**00 1 * * * ./record-the-radio.sh**

Press enter to make a fourth line. (crontab requires a linefeed after the last line)
It should look like this:
```
# m h  dom mon dow   command

00 1 * * * ./record-the-radio.sh


```

Type ctrl-o to save and then ctrl-x to exit.

**6)** Leave the computer on and go to sleep. 

Yup. That's it. Crontab will now do what it is told at the appropriate time. Any failures will always be because of spelling or syntax errors in the crontab or bash script. I hope this helps, and apologies if I left anything out or made typos.

---

