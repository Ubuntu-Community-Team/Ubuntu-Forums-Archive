---
title: "YES there is video chat for linux!"
date: 2008-05-10
forum: The Cafe
---

### Post by barbedsaber on 2008-05-10
With all this talk of funpidgin, I realized that a lot of people don't know of kopete. It is an IM client, separate from pidgin (and funpidgin) IMHO it is buggier, slower and less easy to use than pidgin, and it doesn't support GTalk (XMMP) BUT it has video support.

you can get it by running ```
sudo apt-get install kopete
```

if, when you try and use video, it gives an error about some jasper related thing, then run

```
sudo apt-get install libjasper1
```

or

```
sudo apt-get install libjasper-runtime
```


I'm not sure which one fixes it, but I got both of them, and 1 of them does the job.

now,  I am waiting to see what happens first, if pidgin gets video working, or kopete gets Gtalk working, whichever one it is, will become my full time IM client.

---

### Post by Ub1476 on 2008-05-10
I don't think Pidgin ever will get anything Voip like, cause they're trying to be simple and just sticking to IM.

---

### Post by MaindotC on 2008-05-10
Oh god if I could get a gtalk client that works it would be my day.  So many chicks trying to get in touch with me...

---

### Post by atomkarinca on 2008-05-10
> **strAlan said:**
> Oh god if I could get a gtalk client that works it would be my day.  So many chicks trying to get in touch with me...

I guess [Jabbin]("http://sourceforge.net/projects/jabbin") should get the job done.

---

### Post by Tomatz on 2008-05-10
Amsn

Skype

Ekiga

Kopete

They all support video chat IMO amsn is the best but skype obviously has better video quality.

---

### Post by barbedsaber on 2008-05-10
Ok, so the title should be
YES there is video chat over IM (not voip) for non MSN protocols,  like yahoo.

---

### Post by MaindotC on 2008-05-10
> **atomkarinca said:**
> I guess [Jabbin]("http://sourceforge.net/projects/jabbin") should get the job done.

No, it won't :(

> **Tomatz said:**
> Amsn

Skype

Ekiga

Kopete

They all support video chat IMO amsn is the best but skype obviously has better video quality.

Sure once I get my friends to buy into Skype I'll do that.  I only found Kopete in source could and some of the people to whom I speak use Windoze which means getting them to compile and install is like pulling teeth.

---

### Post by Tomatz on 2008-05-10
> **strAlan said:**
> No, it won't :(



Sure once I get my friends to buy into Skype I'll do that.  I only found Kopete in source could and some of the people to whom I speak use Windoze which means getting them to compile and install is like pulling teeth.

In a terminal:

```
sudo apt-get install amsn
```

Then you will have a fully compatable msn/windows live client ;)

---

### Post by Sef on 2008-05-10
>  Originally Posted by Tomatz  View Post
Amsn

Skype

Ekiga

Kopete

They all support video chat IMO amsn is the best but skype obviously has better video quality.

Also Gyachi, a yahoo clone, does too.

---

### Post by loell on 2008-05-10
whoever said it didn't have video chat? ;)

even flash based video chat works!

---

### Post by vishzilla on 2008-05-10
Pidgin does plan to include A/V support. Check out this [[link]]("http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo")

---

### Post by bash on 2008-05-10
[Galaxium](http://code.google.com/p/galaxium/) is working on Jabber Audo & Video. I think Gajim was working on Jabber A/V as well. But don't know what happened to that.

---

### Post by Johnsie on 2008-05-10
All these programs are ugly looking. What is it with Linux and bad gui?

---

### Post by TheS0urce on 2008-05-10
Best for video chat on linux is on a site, you don't have to install any software.  As long you have flash working it's good to go. 

[www.voiceandvideochat.com](www.voiceandvideochat.com)

You can make your own room with password so you can chat privately.  It is free and the sound is pretty good also.

---

### Post by Tomatz on 2008-05-10
> **Johnsie said:**
> All these programs are ugly looking. What is it with Linux and bad gui?


With linux you get the basic package then you are _free_ to make the program look how _YOU_ want.

Amsn supports skins go to the homepage to download them.

Pidgin integrates with your GTK theme so if you have an ugly desktop go to gnome-look to customise it.

;)

---

### Post by Triscuit713 on 2008-05-10
Empathy currently provides voice support for Gtalk. I use it to talk, although sometimes the voice is choppy.

I can try to help you get it working, provided you do the following:

Start "gksu synaptic" vis the terminal.
Go to Settings->Repositories
Go to Third Party Software
Hit add.
Hit custom.
Enter in this line:

deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main

After this information is added to synaptic, it should be reflected in the list of Third Party Repositories.

Close this dialog box.
Hit reload in the main synaptic gui.
You want to install Empathy 0.23.1, telepathy-gabble 0.7.4, and telepathy-stream-engine 0.5. Any versions older than these will not allow Gtalk/Jingle VOIP.

What has proved problematic for me is helping people get their mic working. This is how I got my mic working.

Ensure that System->Preferences->Sound->Audio Confrencing->Sound Capture uses PulseAudio for input.

[IMG]http://userpages.umbc.edu/~cetris1/Screenshot-Sound_Preferences.png[/IMG]

Install padevchooser either via synaptic or with the line
```

sudo apt-get install padevchooser

```

Then click Applications->Sound and Video->Pulseaudio Device Chooser

You'll see a jack in the notification area of your desktop

[IMG]http://userpages.umbc.edu/~cetris1/Desktop.png[/IMG]

Left click (Yes, left click. This behavior is odd.) on the jack to reveal a menu. 
Click on "Volume Meter (Recording)"
Speak into your mic.

The meter should reflect your voice.

[IMG]http://userpages.umbc.edu/~cetris1/Screenshot-Pulseaudio_Volume_Meter.png[/IMG]

Notice in my screenshot, it says "hw:1 (USB Audio) via DMA". The volume meter reflects the input of the default source, which I have set to my USB mic. Your window will say something different. If it does not reflect where your mic is connected, you will have to change what Pulseaudio calls your default source.

You currently have to enter a string to change the default source. To identify what source you want as your default

Left click on the jack in the notification area
Click "Manager"
Click the "Devices" tab
Make note of the sources available. Everything that is described as "ALSA PCM on ..." is a physical input. Make note of the name representing the physical input associated with your mic (it will always be of the form "alsa_input...").

[IMG]http://userpages.umbc.edu/~cetris1/Pulseaudio-Manager.png[/IMG]

To set your mic as the default source

[B]
Ensure that your mic input is unmuted via the regular gnome volume control. The volume control you are concerned about is on a "Recording" tab, not a "Capture" tab.[/B]

Left click on the jack in the notification area
Click Default Source
Click Other
Enter in the name you took note of before.
Quit and restart the device chooser.

Open the Pulseaudio Volume meter and speak into your mic again. If the default source reflects where you have connected your mic, the volume meter should change


I guess I'm anxious to see other people using it because the more people use it, the more bugs people report. Also, the more people use it, the higher its chances are of being accepted into the next release of Gnome.

---

### Post by csrins on 2008-05-10
Following Triscuit713's instructions, I have installed empathy on a fresh Hardy setup.

However, I face a more fundamental issue: any attempt to connect to a gtalk account fails connection. 

[IMG]http://i128.photobucket.com/albums/p174/csrins/Screenshot-ContactList.png[/IMG]

I am not behind any firewalls, and have seemingly no other network connectivity issues.

Any advice greatly appreciated.

---

### Post by Triscuit713 on 2008-05-11
My first guess is that your name and password are entered incorrectly.

Your name should be "name@gmail.com", not just "name".

---

### Post by EmilyRose on 2008-05-11
And yet none of them interface with AIM/MAC vidoe chat. What gives? I can interface with MAC/AIM video chat with trillian in windows. But NOTHING supports it in linux.

---

### Post by Johnsie on 2008-05-11
The best audio/video apps for linux are actually wengophone, skype and Gizmo. Pigin is pretty useless when it comes to audio/video, amsn has a bad gui with rubbish skins and kopete is buggy on ubuntu. Instant messaging over the major networks is still one of the areas in Linux that is seriously lacking. It's the major IM companies fault for not releasing Linux versions. But knowing who is to blame doesn't do us any good.

---

### Post by the8thstar on 2008-05-11
Re: YES there is video chat for linux!

Cool. Now if only more webcams worked with Linux, this could actually lead somewhere instead of an ugly green screen and crackling sound like you're screaming at someone in the basement. 

"*Houston, we've got a problem..." "Whaaat? Can't hear you, can't see you!"* 

(program crashes)

---

### Post by MaindotC on 2008-05-11
All these posts regarding adding repositories use a hardy repo.  What if I'm waiting for some of the 8 million hardy bugs to be worked out and still using Gutsy?  Can I just replace "hardy" w/ "gutsy" and d/l and install them then?  Have you used Empathy in Gutsy?  What really concerns me is the audio drivers.  I supposed it wouldn't hurt if I download and install ESD or Pulse Audio, but I wanted to check with you guys before I do it.  Thanks!

---

### Post by Tomatz on 2008-05-12
> **strAlan said:**
> All these posts regarding adding repositories use a hardy repo.  What if I'm waiting for some of the 8 million hardy bugs to be worked out and still using Gutsy?  Can I just replace "hardy" w/ "gutsy" and d/l and install them then?  Have you used Empathy in Gutsy?  What really concerns me is the audio drivers.  I supposed it wouldn't hurt if I download and install ESD or Pulse Audio, but I wanted to check with you guys before I do it.  Thanks!


Nope you cant change the url in the apt line because it wouldn't be pointing anywhere. Also the repository would conflict with your package lists and probably break your system.

If the package isnt in your repos even after enabling 3rd party software in system, admin, software sources you can compile the app from source.

Any probs compiling, post back ;)

---

### Post by FuturePilot on 2008-05-12
Actually that Telepathy repository has a Gutsy version.

---

### Post by Triscuit713 on 2008-05-12
Voice and Video did not become enabled by default for Empathy until 0.22.1. The Gutsy version offered at that repository is 0.22, so you don't get jingle audio/video.

---

### Post by MaindotC on 2008-05-12
> **FuturePilot said:**
> Actually that Telepathy repository has a Gutsy version.

So I can modify my sources.list as I mentioned above?  I mean - I'm just asking because I'm trying to research this as much as possible before I dive in.

---

### Post by FuturePilot on 2008-05-12
You could but video probably won't work. See the post above yours.

---

### Post by MaindotC on 2008-05-13
My bad.  Thanks for the clarification.

---

### Post by kyleskimskate on 2008-12-14
ok so why doesn't my camera work with kopete? no error message or anything, just no preview in the configuration box for video. I use an eye toy as my camera btw

---

### Post by tandemcrash on 2008-12-23
empathy doesn't do video chat or even voice call... it doesn't even say anything about these features in the help. useless post!!

---

### Post by MikeTheC on 2008-12-24
> **the8thstar said:**
> Re: YES there is video chat for linux!

Cool. Now if only more webcams worked with Linux, this could actually lead somewhere instead of an ugly green screen and crackling sound like you're screaming at someone in the basement. 

"*Houston, we've got a problem..." "Whaaat? Can't hear you, can't see you!"* 

(program crashes)
Oh, one can only imagine...

[indent]Phone Rep: Thank you very much for calling Sony Manned Spacecraft Technical Support. My name is John. May I be having your number of the phone beginning, please, with area code?

Astronaut: This is spacecraft commander Jim Lovell. I'm aboard Apollo 13, and we've had a problem.

Phone Rep: Yes, I need the phone number beginning with your area code, please.

Lovell: Phone number? What? Look, we're on a spacecraft heading for the Moon, for Chrissake, something's just gone horribly wrong, and you want my phone number?

Phone Rep: Very much, sir. Beginning with...

Lovell: Yes, yes, I know...

Both: ...the area code.

Lovell: I don't think you understand. We're all about 200,000 miles away from the nearest telephone.

Phone Rep: Then how, sir, if I may be asking you now as you are talking to me, did you call technical support?

Another Astronaut: Look, this is Fred Haise. We've had some bangs, and we've got a wicked shimmy up here right now...

Phone Rep: Pardon me, are you calling about the same Sony spacecraft product?

Haise: We both are, darn it!

Phone Rep: Well then, Mr. Haise, would you be so good as to provide me a phone number starting with the area code? The other gentleman was sadly reluctant to be forthcoming...

Haise: We don't have a d**n phone. Lookit, we're talking to you on a headset connected to the spacecraft radio. And it doesn't have a phone number, either.

Lovell: Why do you want a phone number?

Phone Rep: I'm sorry, sir, you're not coming through correctly. Perhaps you have another extension you could use instead?

Lovell: There's only three headsets, each of us is using one. Now, we're in distress and we need help. Could you please put down the script and help us?

Phone Rep: Oh, I'm very much being sorry about that, but I must ask you for your phone number. We cannot begin the call without one.

Swiggert: Hang on a second here. One darned second. I don't know if you're copying us, but we're having a life-threatening problem here. We're fighting just to keep from tumbling off-course, we've got just tons of thruster activity up here, and you're telling us you can't begin this call without a phone number? We're already talking to you. So it seems like we've skipped that part. So can you just give us some basic support without the hassle?

Phone Rep: Hmm...

*thinks about this, actually wonders how he could have had this call without yet having obtained a phone number (beginning, of course, with the area code)*

Phone Rep: Well, I may place you on hold for just a moment while I speak with my supervisor about this?

Lovell: What? Put us on hold?

Phone Rep: That is correct, sir.

Haise: So you can ask your supervisor if it's alright for you to help us to keep from dying here in the next few minutes, possibly, without a phone number?

Phone Rep: That is correct, sir.[/indent]

---

### Post by stiffler665 on 2009-09-19
*chuckle*
That was pretty funny. A+ for creative writing!

---

