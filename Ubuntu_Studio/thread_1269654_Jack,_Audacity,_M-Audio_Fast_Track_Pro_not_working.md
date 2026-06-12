---
title: "Jack, Audacity, M-Audio Fast Track Pro not working right"
date: 2009-09-18
forum: Ubuntu Studio
---

### Post by g-raf on 2009-09-18
I'm using qjackctl + audacity to record audio through an m-audio fast track pro usb soundcard. I have Jack set to "duplex" in the audio settings and i have audacity set to capture stereo tracks, however, only the left track is captured when i record. I'm wondering how i can capture both stereo tracks when recording. I got so excited about fixing this problem that i made [a vlog about it (click here to download mp4)]("http://www.archive.org/download/VlogAboutUbuntuStudioJackAudacityUsbSoundcard_289/vlog1.mp4"), using Istanbul Desktop Session Recorder, Cheese Webcam Booth and Kdenlive.

---

### Post by cooper77z on 2009-09-18
Look for those small clickable icons and the preferences menus.

---

### Post by raboofje on 2009-09-19
> **g-raf said:**
> i have audacity set to capture stereo tracks, however, only the left track is captured when i record. I'm wondering how i can capture both stereo tracks when recording.

The 2 inputs on the front of the device are 2 balanced inputs - 2 mono inputs that together combined are one stereo input.

It looks like you're recording in stereo, but you're only providing input into the left input. It makes sense that you get a silent 'right' track, then, no? :).

If you want to have the input mixed over both channels, you might try switching the 'mono/stereo' button - I'm not sure if this one applies only to the headphone monitoring or also to the outputs. It might make more sense to just set Audacity to 'mono', though.

---

### Post by g-raf on 2009-09-19
> **raboofje said:**
> The 2 inputs on the front of the device are 2 balanced inputs - 2 mono inputs that together combined are one stereo input.

It looks like you're recording in stereo, but you're only providing input into the left input. It makes sense that you get a silent 'right' track, then, no? :).

If you want to have the input mixed over both channels, you might try switching the 'mono/stereo' button - I'm not sure if this one applies only to the headphone monitoring or also to the outputs. It might make more sense to just set Audacity to 'mono', though.

I tried the mono/stereo button, but it only applies to the headphones. I prefer to record in stereo so that i can manipulate the left/right tracks differently. I might need to switch some alsa settings so that both mic inputs are recognized as two stereo tracks each, right?

---

### Post by g-raf on 2009-09-19
In System>Preferences>Sound the default mixer is set to HDA Intel (ALSA) whereas the playback and capture devices are set to the usb soundcard. The usb soundcard isn't listed among the default mixer devices. How can i get the usb soundcard recognized as a default mixer device using alsa?

---

### Post by g-raf on 2009-09-19
Also, in alsamixer, the "usb audio" has nothing - no mic or capture, no master volume, nothing. I'm wondering how can i get the m-audio fast track pro recognized as a default mixer device.

---

### Post by g-raf on 2009-09-19
I've been googling and searching in forums and it seems like setting usb audio to be able to record in both stereo tracks (in ALSA) is still unresolved. Can anyone offer an idea about what i can configure in order to capture two stereo tracks on two mic inputs?

---

### Post by g-raf on 2009-09-19
When i try > cat /proc/asound/card0/stream1 in the terminal, it gives me this: 

> M-Audio FastTrack Pro at usb-0000:00:1d.0-1, full speed : USB Audio #1

Playback:
  Status: Stop
  Interface 3
    Altset 1
    Format: 0x2
    Channels: 2
    Endpoint: 4 OUT (ADAPTIVE)
    Rates: 44100

Capture:
  Status: Stop
  Interface 4
    Altset 1
    Format: 0x2
    Channels: 2
    Endpoint: 5 IN (ASYNC)
    Rates: 8000 - 48000 (continuous)


I want to configure the capture setting to two inputs with a total of four channels. What kind of file should i "sudo gedit" in order to configure these settings?

---

### Post by raboofje on 2009-09-19
> **g-raf said:**
> it seems like setting usb audio to be able to record in both stereo tracks (in ALSA) is still unresolved. Can anyone offer an idea about what i can configure in order to capture two stereo tracks on two mic inputs?

Well, the mic inputs *are* mono inputs. 

So you want to record this mono input, and then create a stereo track out of it, applying different manipulations to the left and right tracks.

Isn't it possible to do just that? First record 1 mono track, then split that track into a stereo project?

---

### Post by g-raf on 2009-09-20
> **raboofje said:**
> Well, the mic inputs *are* mono inputs. 

So you want to record this mono input, and then create a stereo track out of it, applying different manipulations to the left and right tracks.

Isn't it possible to do just that? First record 1 mono track, then split that track into a stereo project?

I would like to do that, but how is that possible in Audacity? I see there is an option for "make stereo track" but i can't select that, as is shown in this screenshot:
[IMG]http://blog.jinbo.net/files2/72/giraffe/images/200909/200918315.jpg[/IMG]

---

### Post by raboofje on 2009-09-20
* record a mono track
* duplicate that track: select the whole track (by clicking on the 'mono xx hz xx bits' part), copy (ctrl-c), unselect it (by clicking outside it), paste (ctrl-v)
* now 'make stereo track' is available on the upper track, it'll combine the 2 mono tracks into 1 stereo track

---

### Post by g-raf on 2009-09-20
> **raboofje said:**
> * record a mono track
* duplicate that track: select the whole track (by clicking on the 'mono xx hz xx bits' part), copy (ctrl-c), unselect it (by clicking outside it), paste (ctrl-v)
* now 'make stereo track' is available on the upper track, it'll combine the 2 mono tracks into 1 stereo track

I've done this and found that if I mute (add silence) part of the left track before clicking "make stereo track," that there is no audio coming from the right track. So it's not making a real stereo track that plays audio from both tracks. Anything else i should try?

---

### Post by raboofje on 2009-09-20
> **g-raf said:**
> if I mute (add silence) part of the left track before clicking "make stereo track," that there is no audio coming from the right track. So it's not making a real stereo track that plays audio from both tracks.

Are you sure? This seems to be working fine for me: recorded some noise, copied it, deleted part of the upper track, then chose 'make stereo track'. Sure enough, when played, the left volume drops when it reaches the part that was cut out... not sure what we're doing differently here.

---

### Post by g-raf on 2009-09-20
I just produced a [10-min vlog about this problem (click here to download)]("http://www.archive.org/download/Vlog2AudacityJackUsbSoundcard/vlog2.mp4") of ALSA recognizing the two input mics as left/right, not as separate mono or separate stereo tracks.

---

### Post by raboofje on 2009-09-21
I don't quite understand what you're aiming to do.

In the vlog, where you do an 'insert silence', aren't you doing exactly what you want there? Manipulating the left channel independently from the right channel?

---

### Post by cooper77z on 2009-09-21
Audacity can be a pain, but then again it is a really great program if one uses  it to ones advantage. Give it some time. Maybe the program creators will support your hardware better in the future.

---

### Post by g-raf on 2009-09-21
> **raboofje said:**
> I don't quite understand what you're aiming to do.

In the vlog, where you do an 'insert silence', aren't you doing exactly what you want there? Manipulating the left channel independently from the right channel?

When i make silence in the left channel, then the right channel is also silent - no sound from the right speaker, no sound at all. So when i make a stereo track from duplicating the left channel, that doesn't allow me to manipulate the channels separately after selecting 'split stereo track.' 

More than anything else, this is what I'm aiming to do: record 1 stereo track from 1 mic input. I'm hoping this is possible by reconfiguring ALSA, but so far, I haven't found any information about it.

---

### Post by g-raf on 2009-09-21
> **cooper77z said:**
> Interesting discussion. To me, it seems like you are too stupid to use the program and then you want to complain about it because you just don't get it.

I've been using Audacity for 10 months now and understand how to use it. However, there is still much to learn. I'm not complaining about Audacity, ALSA or Jack. There are some problems with the way these programs run with the M-Audio Fast Track Pro usb soundcard and I'm interested in exploring solutions to these problems, but I'm certainly info-starved when it comes to experimenting with potential solutions. Sorry if I might have offended you.

---

### Post by cooper77z on 2009-09-21
I am the one who should be appologizing. I am sorry, and I am going to edit my post now. Would it be worthwhile for you to purchase a soundcard that audacity supports?

---

### Post by g-raf on 2009-09-21
> **cooper77z said:**
> I am the one who should be appologizing. I am sorry, and I am going to edit my post now. Would it be worthwhile for you to purchase a soundcard that audacity supports?

Audacity is running on Jack and Jack is running on ALSA as a driver. ALSA uses the ["usb audio" module]("http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio") for the M-Audio Fast Track Pro. I'm simply wondering how i can reconfigure the module so it recognizes the two mic inputs (on the Fast Track Pro) as separate stereo track recording devices.

---

### Post by g-raf on 2009-09-21
I'm also wondering how i can use this patch and if it will make ALSA recognize each mic input as a separate stereo track. I found a link to an M-Audio Fast Track Pro patch for ALSA: [http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro)

---

### Post by sgx on 2009-09-21
Hi, use the copy/paste icons in the gui. Import or record your first stereo or mono track. Then create a new stereo or mono track, select your recorded audio, click the copy icon, click the new track where you want it duplicated, then click the paste icon. There is a 'duplicate' command that is easier for some things. The 'select options are in the Edit menu,
about 2/3 down from the top. 
Cheers

edit of course, you can apply separate fx to each duplicated track, pan one mono track hard-left, the other hard-right, if you should desire separation, and a quasi stereo field.

---

### Post by g-raf on 2009-09-22
> **sgx said:**
> Hi, use the copy/paste icons in the gui. Import or record your first stereo or mono track. Then create a new stereo or mono track, select your recorded audio, click the copy icon, click the new track where you want it duplicated, then click the paste icon. There is a 'duplicate' command that is easier for some things. The 'select options are in the Edit menu,
about 2/3 down from the top. 
Cheers

edit of course, you can apply separate fx to each duplicated track, pan one mono track hard-left, the other hard-right, if you should desire separation, and a quasi stereo field.

I know how to do that, but I wouldn't know how to do this: if i record an interview with two people, one person on each mic. I'm guessing i should just give up and try recording in mono in such circumstances. What if there are two vocalists recording a song and i want to edit both of their tracks separately? If i record a stereo track with the two mics, then one track is recorded on the left and the other track on the left channel. Then should i "split stereo track," duplicate both tracks and create two separate stereo tracks out of what was one stereo track? I haven't tried it yet, but i hope this will work.

---

### Post by g-raf on 2009-09-27
I just figured out how to record stereo tracks out of the Fast Track Pro mic inputs using Jamin and Audacity. If anyone is having similar problems doing this, please watch this 2-min "how to" video: 

[http://www.archive.org/download/UbuntuStudioSoundChronicles1/UbuntuStudioSoundChonicles1.mpg](http://www.archive.org/download/UbuntuStudioSoundChronicles1/UbuntuStudioSoundChonicles1.mpg)

---

### Post by raboofje on 2009-09-27
> **g-raf said:**
> I just figured out how to record stereo tracks out of the Fast Track Pro mic inputs using Jamin and Audacity. If anyone is having similar problems doing this, please watch this 2-min "how to" video: 

[http://www.archive.org/download/UbuntuStudioSoundChronicles1/UbuntuStudioSoundChonicles1.mpg](http://www.archive.org/download/UbuntuStudioSoundChronicles1/UbuntuStudioSoundChonicles1.mpg)

Good to hear you've got this working to your satisfaction.

mplayer is having trouble playing that file though: the video is ok, but the audio is full of silences, screeches and the occasional fragment of normal speech. Your previous mp4's were fine.

---

### Post by kayosiii on 2009-09-27
> **raboofje said:**
> The 2 inputs on the front of the device are 2 balanced inputs - 2 mono inputs that together combined are one stereo input.

Balanced inputs are not stereo inputs - A balanced input carries a signal and the inverse of the signal on two separate wires. These are combined at the other end and this helps eliminate interference picked up along the wire.

Connecting a stereo source to a balanced input is going to cause you no end of confusion.

---

### Post by raboofje on 2009-09-28
> **kayosiii said:**
> Balanced inputs are not stereo inputs - A balanced input carries a signal and the inverse of the signal on two separate wires. These are combined at the other end and this helps eliminate interference picked up along the wire.

Yes.

> Connecting a stereo source to a balanced input is going to cause you no end of confusion.

That's not what this discussion is/was about: g-raf is connecting a mono input (his microphone) to the port, but wants it to show up in audacity as a stereo stream for some reason.

---

### Post by g-raf on 2009-09-29
> **raboofje said:**
> g-raf is connecting a mono input (his microphone) to the port, but wants it to show up in audacity as a stereo stream for some reason.

Because i like to have the option of panning vocal, instrument, etc. recordings.

---

### Post by dawiba on 2009-09-29
I realise I'm joining this very late, but hopefully this will help.

You can not record stereo from a mono input. You can record from a mono source into a stereo track, but you won't get stereo. You'll get double mono. This is probably close enough to what you're trying to get.

The good news is that this is really simple in Ardour.

Launch Jack and click the 'Start' button. Launch Ardour, select new session and name it and then open it. You'll now have an Ardour window open with a master track. Go to the top and select 'Track' -> 'Add Track/Bus'. In the pop up window that appears, choose stereo track from the 'channel configuration' drop down. Leave 'track mode' as 'normal'. Click on 'add'. You should now have a new stereo track ready to use.

Next go to Jack and click on the 'Connect' button. In the window that appears, you will find some connections already made for you. From the left hand window, choose the output that is your mic output and select it by clicking on it once. It will now be highlighted. It will probably be connected to 'Audio 1/In 1' in the right hand window. If it isn't, connect the two by highlighting them and clicking the 'Connect' button. Next select your mic output from the left window and 'Audio 2/In 2' from the right window and connect them as well, so that your mic output is connected to the two track inputs simultaneously.

Back in the Ardour window, record enable your stereo track by clicking on the red button on the track. Next, click on the red record button on the transport bar at the top. This one will now be flashing. Next, press play and start recording.

You will now have your mono mic recorded to a stereo track, although it's not true stereo. If you want two channels (therefore tracks) to add effects to separately, do as above but instead of creating one stereo track, create two mono tracks and make sure your mic input is connected to each track as before. Remember to record enable both tracks before hitting record on the transport.

The only difference, is that you will see your recording now as two mono tracks instead of one stereo track. The end result is the same, double mono.

Incidentally, I couldn't get this to work in Audacity, which is why I'm recommending Ardour.

---

