---
title: "No sound in Nted (NoteEditor)"
date: 2009-05-06
forum: Ubuntu Studio
---

### Post by Boludinux on 2009-05-06
Hi guys, I'm trying to run this notation program Nted (1.4.17 from the Jaunty repositories) but it doesn't give me any sound output. 

I have read the FAQ in the manual ([here]("http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/doc/apa.html#id322509")), but I could not find anything that helps me, and since I can play midi files in Timidity for example I'm assuming that theres something wrong with the program... anyone has had any issues with this?

Thanks.

---

### Post by low_impact on 2009-06-02
use the application manager to install timmidy and it should work for you then.

---

### Post by RabbitWho on 2010-01-22
The original poster clearly stated he had timidity already and that he could play midi files in that.

I  have the very same problem. 
I went to configure in Nted and selected all the various timidity options and still no sound. 

Anyone any ideas?

---

### Post by RabbitWho on 2010-01-23
bump!

---

### Post by kb2tfa on 2010-01-23
same here no sound

---

### Post by RabbitWho on 2010-01-23
It said something in the FAQ about some soundcards not supporting midi,  but surely it must since I can save the tunes I write in Nted and then listen to them in another program, I just can't listen to them live as I write them in nted.

---

### Post by kb2tfa on 2010-01-23
> **RabbitWho said:**
> It said something in the FAQ about some soundcards not supporting midi,  but surely it must since I can save the tunes I write in Nted and then listen to them in another program, I just can't listen to them live as I write them in nted.

I know right. what's up with that.

I can write the music, but have to export as midi in order to listen to it.

I read some docs that showed to edit midi settings for a specific port, however I cannot edit my midi settings. It only shows the port, no way to edit.

But as you were saying you can't listen live, same here. I'll just write and export to listen, I suppose.

---

### Post by RabbitWho on 2010-01-24
:( I'm not Beethoven, I kinda need to hear what I'm doing. 


I might *shudder* boot into windows and see if I can get it to work there.

---

### Post by jackdale on 2010-02-27
I use Sibelius 5 on Mac OS X 10.6

I downloaded NtEd because it seemed like it might have similar functionality (albeit without easy compatibility!).  I would love to be able to write my music in Ubuntu.  Unfortunately, I have the same problem.

Notes are obviously "playing" (red notes), but without sound.  I can export to midi with no problem.

As noted previously, I find it "interesting" that the guy says that if we can't hear the playback, it has nothing to do with his program...  (Why is it that every other program that needs midi is able to find it and use it?)

---

### Post by kb2tfa on 2010-02-27
I gave up on it, and use tuxguitar

---

### Post by jackdale on 2010-03-13
> **kb2tfa said:**
> I gave up on it, and use tuxguitar

I thought tuxguitar only did guitar + tab...

---

### Post by cefn on 2010-06-12
If there's anyone willing to try, I suspect that adding the packages...

timidity
timidity-daemon

...and their choice of 'soundfont' packages will succeed in the end.

The suggested soundfont installs to install along with timidity are 

fluid-soundfont-gm
fluid-soundfont-gs

Some ubuntu users will encounter this bug...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/531733](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/531733)

Which requires you to add the timidity user to the pulse and pulse-access groups. Instructions are on the referenced page. After giving timidity access to the pulse subsystem (which is ubuntu's audio system) the daemon can launch and translate midi into sound for you.

Dont be too hard on the Nted developer. I think he's right. This explanation may help.

Although Nted was initially silent, after installing timidity, fixing it, and adding some soundfonts. I chose a suitable midi channel using the Nted menu Edit=>Preferences=>Configure midi out (I chose 128:0 listed as a timidity channel). Then I could hear the melodies being played by Nted.

You may notice in the timidity information within Synaptic...

> TiMidity++ is a very high quality software-only MIDI sequencer and MOD player. It uses sound fonts (GUS-compatible or SF2-compatible) to render MIDI files, which are not included in this package.

...which may explain how even a fully installed version of Timidity may  still be silent without soundfonts.

It's also worth nothing that if your soundfonts don't have samples for the voices you have chosen in your midi selection, then some voices will be silent. 

For example I had an audible guitar, but an inaudible voice track having imported Daisy Bell from MusicXML. Right-clicking on the start of the stave in Nted, and choosing a different midi instrument for the voice track made it work. 

There are two explanations for how other midi programs work, whilst a score in Nted is silent. It may be that the other programs have chosen voices which you actually have soundfonts for.

The other part of the explanation is that a MIDI file loaded and played interactively by your user account can trigger the synthesis itself, whilst the timidity daemon is actually another program listening on a midi output channel, and the daemon itself (running as a user called timidity) needs its own access to the soundcard to make noise. The fact the timidity user is not added to the pulse and pulse-access groups is a bug.

---

### Post by aduplat on 2010-08-08
Hi there:

This works for me:

[http://ubuntuforums.org/showthread.php?t=770148&page=2]("http://ubuntuforums.org/showthread.php?t=770148&page=2")

Specifically:

> 1. Launch Timidity++ as server with this command from Terminal:

timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &

2. Open NoteEdit, go to Setting -> Configure -> Sound and select "Timidity port 0 128:0", "Apply" then "OK"

Now pressing the play button it should work.

Found this here:

[http://alsa.opensrc.org/index.php/Ti..._with_Noteedit](http://alsa.opensrc.org/index.php/Ti..._with_Noteedit)


---

### Post by Jack Brown on 2010-10-08
works! (also posted this in the other thread)

In lucid & nted (1.9.16 by Joerg Anders)

 1. install timidity (if not yet installed)
 2. Open terminal and run: timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &

terminal will display something like: Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 2048, period size 680 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 131:0 131:1 131:2 131:3

and a flashing cursor

3. go to nted menu: EDIT->Preferences > configure midi out
- i think u can select any of the ports displayed on your terminal.  i tried: 131:0 Timidity and 131:1 Timidity, both worked.

now the next step would be to make it work the first time nted is run on  the session (ideally not on startup: keeping it lean.)  

how do we do that?

---

### Post by Pablo_F on 2010-10-08
> now the next step would be to make it work the first time nted is run on the session (ideally not on startup: keeping it lean.) 

A simple bash script should do it.

$ mkdir ~/bin
$ cd ~/bin
$ gedit nted-timidity

Add the following. Lines preceded by # are comments that you can omit, except for the first line.

#!/bin/bash
# my command to start timidity (I mean, your command)
timidity -iA -B2,8 -Os -EFreverb=0 2>&1 &
# Wait three seconds
sleep 3
# now, nted
nted

Save and close gedit.

Now, give the script execution permission:

$ chmod +x nted-timidity

You have created a new command. Test it:

$ nted-timidity

If it works, you can add a custom launcher with this command or if you prefer to launch nted the usual way from the sound and video menu, you can use alacarte:

$ alacarte

Sound and Video, search for nted. Properties. Change command from nted to nted-timidity

Close alacarte and you are done.

Cheers! Pablo

---

### Post by Jack Brown on 2010-10-09
pablo,

that works, thanks. :guitar:    And the explanations for the commands made it clearer, letting me know what i was typing in the terminal.

Still need to select the configure midi out option in nted though...  but am content with this.... just got to tell other pc users.


hmm i ran the timidity script i got additional ports for timidity but i was in a different user account..
default one was 128 right?, now ive got an additional 129 with the 131...  
might that make the list long and cluttered if you have many users? or maybe it's designed that way....

good day.

---

### Post by Pablo_F on 2010-10-09
It could be that timidity daemon is launched automatically for that user so they end up with two instances of timidity if they run the nted-timidity script. So they don't need it in this case. 

I personally use qsynth (a graphical front-end for fluidsynth) instead of timidity as a general purpose soft synth. Like timidity, it is a soundfont player but much more intuitive to load soundfonts, control volume, add effects, etc.

Cheers! Pablo

---

### Post by Jack Brown on 2010-10-10
hi pablo,

you know what, nted playback works automatically for one user using timidity 128, without the script / alacarte edit. (after updating packages today, if related) or you might be right that some daemon is started by default, and once '128:0 Timidity' is selected it works by itself.   Really nice!  

But then i switched to another user to try it out...  and sound is disabled for that user...


volume icon displays   <---

so users can only use sound one at a time in ubuntu?  not that im complaining, just asking if it normally works that way.

might look into that soundfont program you suggested, but since timidity works, would probably stay with it.  

And nice having a balance of timidity and audacity on my system :P

edit: qsynth does look intuitive... you think it would work in place of timidity?   would try it out sometime.

Ubuntu!

---

### Post by Pablo_F on 2010-10-10
Hi Jack,

I am not a linux expert but this "users and groups" thing is interesting. I have just checked that there is a group called, unsurprisingly, "timidity", so making this user a member of "timidity" group will, hopefully, launch the daemon automatically also for them. 

As for the sound problem with simultaneous users, I googled a bit and this came up:

[http://ubuntuforums.org/showthread.php?t=1417647](http://ubuntuforums.org/showthread.php?t=1417647)

So it turns out that there is another group called, pulse-access and what you have to do is explained in this configuration file: "/etc/default/pulseaudio" (edit with sudo). 

This is what I love about linux. It is not obvious at first sight how to change the conservative behaviour but it tends to be safe by default.

Changes in users and groups need a system reboot.

> And nice having a balance of timidity and audacity on my system

Really! And I might need a bit of ardour with Jack in a rosegarden :P
> 
qsynth does look intuitive... you think it would work in place of timidity?

Yes, it will work but having a daemonized soft synth can be more comfortable for your needs. If you don't dislike its sounds and don't specially need low latency, timidity is your best option. That said, you can change soundfonts in timidity too, but not graphically.

Cheers! Pablo

---

### Post by Jack Brown on 2010-10-18
hi Pablo,

adding the user account to 'timidity' group and then selecting the midi out on nted works like sunshine.

thanks for looking up the pulse audio issue too.  

:popcorn: Hah.. looks like a person can make an interesting story out of the ubuntu/linux package names.  (who knows, maybe someone already did?...)

regards,

J

---

