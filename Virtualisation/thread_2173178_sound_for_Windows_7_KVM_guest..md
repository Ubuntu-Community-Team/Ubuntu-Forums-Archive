---
title: "sound for Windows 7 KVM guest."
date: 2013-09-08
forum: Virtualisation
---

### Post by KillerKelvUK on 2013-09-08
Running clean Ubuntu 13.04 install with KVM and Virt-Manager.  Trying to figure sound out and need some help please...

Host audio works fine, via HDMI.  "aplay -l" confirms card0,device3.

Guest configured using ich6 device in virt-manager...guest boots fine and all device drivers inside work...guest looks like its playing audio with the UI showing output but nothing is heard.

Have modified /etc/libvirt/qemu.conf with

vnc_allow_host_audio=1
user='myuser'
group='myuser'

Looking at the /var/log/libvirt/qemu/Windows7.log the following is the excerpt related to the audio (no errors are reported)

"...device intel-hda,id=sound0,bus=pci.0,addr=0x4 -device hda-duplex,id=sound0-codec3,bus=sound0.0,cad=0..."

How do I specify the correct card and device.  I can edit the domain xml using virsh edit but am unsure of the syntax to use?

Would appreciate any help.

K

---

### Post by KillerKelvUK on 2013-09-10
bump!

Really struggling with this, any suggestions welcome.

---

### Post by TheFu on 2013-09-10
Never expected audio to work over VNC. Does it? Have you seen this before?

I have seen audio work over Spice from a KVM client-OS.  2 machines involved - the pure server KVM host running a Spice-kvm clientVM and a different Windows client running the spice specific remote desktop.

Also, I've never seen this work over NX either, except when I was screwing around with spice.

Sorry, I'm not much help.

---

### Post by TheFu on 2013-09-10
forum error - double-post.

---

### Post by CharlesA on 2013-09-11
> **TheFu said:**
> Never expected audio to work over VNC. Does it? Have you seen this before?

That pretty much echos what I've noticed as well, at least on my Win7 VM. I don't get sound from VNC, but I do get it if I use Windows' remote desktop connection (which is normal).

Not much help here, either.

---

### Post by KillerKelvUK on 2013-09-11
:-) Thank you both for being polite with your responses...I'm new to VNC so had simply assumed it supported audio as RDP does!

Anyways I quickly installed the Remmina Remote Desktop Client from the Ubuntu Software Centre and connected into the guest with ease...except I still have no audio output :-/

I've configured the RDP connection to use "Local" audio, then when I connect to the guest Windows advises there is no audio output device installed...if I configure the RDP connection to use "Remote" audio then the windows guest boots and advises it has a configured audio output device and looks as though its playing audio but I heard nothing!

Have googled around a lot of sites but primarily have attempted variations on a theme based around this link...[http://gurjeet-tech.blogspot.co.uk/2012/09/how-to-install-kvm-with-working-audio.html](http://gurjeet-tech.blogspot.co.uk/2012/09/how-to-install-kvm-with-working-audio.html)

Any ideas where I'm going wrong or what else I've overlooked?

---

### Post by TheFu on 2013-09-11
The only way that I've ever seen remote audio work for Linux systems is with KVM using the Spice VM driver and using the Spice Viewer.  

That is NOT using VNC and NOT using NX.  

It has been about 8 months since I tried to get spice working and it wasn't as stable as I needed, so I'm back to NX.  After you find the spice-howto and follow those instructions, opening a different thread for issues would be best.

Just trying to be clear.  Just because I've never seen it, doesn't mean it isn't possible. We all have different experiences and Linux is impossible to know more than about 10% of.  ;)

---

### Post by KillerKelvUK on 2013-09-11
@TheFu...I'll certainly look more into Spice so thanks for the advice.

However...I have made progress; of a fashion.  I can now get audio from my KVM Win7 guest however it would seem that the guest is completely taking over the audio for my host.  So my process is as follows...

Followed this guide...[http://gurjeet-tech.blogspot.co.uk/2...ing-audio.html]("http://gurjeet-tech.blogspot.co.uk/2012/09/how-to-install-kvm-with-working-audio.html") but have altered the sound configuration of my guest from using 'ich6' to 'ac97', this required me to install the sound drivers for the ac97 codec into the guest, [U][B]I now get audio for my guest even when I haven't yet opened a remote desktop connection!
[/B][/U]
At a guess what I think I have done by taking the above steps is to force the guest to output audio via the ac97 codec, the modifications in libvirt I think have tided my hosts alsa drivers directly to the guest which negates the need for a remote desktop client!  Once the guest has loaded the host sound is then dedicated to the guests output, the only way I can get host 'internal' audio working is to shutdown the guest and then issue a 'sudo alsa reload'.

"Shot in the dark here..." -->  However I noticed in the Sound Settings panel that whilst the guest is running if I attempt to switch the host audio output device then a new "dummy" device is inserted in the list which I can't deselect, once I've stopped the guest and issued 'sudo alsa reload' this additional "dummy" device disappears and my host internal audio is back to normal.  Some of my googling has found very similar symptoms as this but where they are generic audio issues with 13.04 and nothing to do with VM's, could this be a confusion factor I can easily debug and remove?

Is this worth my time debugging as your feedback and the googling that I've been doing doesn't seem to give much certainty/confidence around vm guest audio, if the generally adopted route is to use Spice then I'm happy to abandon my current efforts if futile?  (As I'm still learning linux and vm's this kind of problem really helps me to gain knowledge as they force me to learn but conversely I don't want to waste my time on a trodden path that goes nowhere!)

---

