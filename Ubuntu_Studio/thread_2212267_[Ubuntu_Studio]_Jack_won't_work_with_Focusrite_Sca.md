---
title: "[Ubuntu Studio] Jack won't work with Focusrite Scarlett 2i4"
date: 2014-03-20
forum: Ubuntu Studio
---

### Post by tim-staat on 2014-03-20
Hey Guys,

my Jack does not always recognize my Scarlett 2i4. On Startup it gets the MIDI Ports but not the other (analog audio) ports, which are the important ones for me: [ATTACH=CONFIG]251318[/ATTACH].

In non-deterministic cases it recognizes the audio Ports as JACK Source (input) and JACK Sink (output), but trying connecting them, i'll receive multiple errors and callbacks: [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=251319&stc=1&thumb=1&d=1395320135[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=251319&d=1395320135").

Hope anyone can help, and thanks in advance! 

Tim

---

### Post by jejeman on 2014-03-20
Well, why didn't you show us the Audio tab how it looks?

Do not expect to see in Audio tab audio ports to be named by the sound card name. It is always system_playback and system_capture or similar.

---

### Post by tim-staat on 2014-03-20
Hey,

thanks for your quick response!

The table: [ATTACH=CONFIG]251323[/ATTACH].

This fits to the ports of the 2i4. But if i disconnect the audio interface and refresh the connection screen, there still are system in & outs provided...

And if i just connect in and out, the inout should just go through the output? But this does not work either...

---

### Post by jejeman on 2014-03-20
I don't see anything wrong in Audio tab. Alles in ordung.

Never disconnect Audio device while JACK is running. Refresh is only for software applications, not for system devices.
If you disconnect Audio device it is expected JACK to crash or hang if you do that, you need to restart JACK server. So, never disconnect audio device while JACK is running.

Now, kill JACK, plug in audio device, start JACK and try it. Connecting directly IN to OUT should give you monitoring of the inputs. It should work, you should hear sound from input on the speakers.

---

### Post by tim-staat on 2014-03-20
Hey,

again thanks for your very useful answer! I'm kinda stupid: i thought, system means the internal speaker and mics of th notebook ["the system"]. I'm very happy finally it was just my own stubborness and not a hardware error... :)


Thanks for it! :)

---

### Post by su:bhatta on 2014-03-21
Welcome to the world of Linux for creative humans .Glad you got that sorted out.

You can mark this thread as 'Solved' using the 'Thread Tools' at the top right of the page.

---

### Post by jejeman on 2014-03-21
> **tim-staat said:**
> i thought, system means the internal speaker and mics of th notebook ["the system"].No, system means what ever audio card was chosen for JACK server.

---

