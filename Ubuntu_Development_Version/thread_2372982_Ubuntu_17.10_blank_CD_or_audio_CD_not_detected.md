---
title: "Ubuntu 17.10 blank CD or audio CD not detected"
date: 2017-10-01
forum: Ubuntu Development Version
---

### Post by corradoventu on 2017-10-01
When I insert a data CD or DVD I have a notification and I see the CD in files. 
With audio CD nothing happens.
Also empty CD and DVD are not detected.
No problem on same PC, different partition with Ubuntu 16.04.
I have the same problem on 3 different PC running Ubuntu 17.10.
I opened a bug about this problem: [https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/1720624](https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/1720624)
did You have the same problem?

---

### Post by jbicha on 2017-10-01
By the way, Ubuntu does not include an app for CD/DVD writing by default. I suggest brasero or k3b.

---

### Post by corradoventu on 2017-10-01
The problem is not the application, and I don't want WRITE CD or DVD, The problem is that the Audio CD IS NOT DETECTED at all!

---

### Post by mc4man on 2017-10-01
Can't say that I see that here, fresh install latest image

---

### Post by mc4man on 2017-10-01
That being said it seems handled very poorly.
1. Sometimes takes a very long time, 30 - 120 secs on internal drive
2. 2 - 3 min on a usb drive
3. No notification
4. The setting on how to handle audio cd insertion is 'ignored'
5. Icon doesn't always show up on Desktop
6. In repeated tests in same session they are never opened, internal or external

---

### Post by mc4man on 2017-10-01
To further how 'bad' it is screen shows audacious (2 instances) 1 playing /dev/sr0, 1 playing /dev/sr1 yet no sign of either disc in nautilus or the desktop
So maybe the issue is with gvfs? (screen 2 shows error when attempting to browse to cdda://dev/sr0 while cd is already available to audacious at that location

---

### Post by Frogs Hair on 2017-10-01
I found my audio disk volume in other locations and selected it to mount and was then able open in rhythm-box. No auto play though and the disk utility sees both the player and cd volume.

---

### Post by corradoventu on 2017-10-01
in other locations? where?

---

### Post by Frogs Hair on 2017-10-01
In the file manager other locations, oddly my movies show up as expected in the left pane of the file manager when loaded in the player.

Edit: Our problems may not be related if the disk utility doesn't detect the CD/DVD drive.

---

### Post by mc4man on 2017-10-01
I've never seen audio cds in 'other locations', just the sidebar. (screen
Most reliable way here is to insert disc, wait about 10 -15 secs, then log out/in. Usually then is the sidebar. 

audio cds are probably considered 'depreciated'

---

### Post by Frogs Hair on 2017-10-01
> [COLOR=#000000]I've never seen audio cds in 'other locations', just the sidebar.[/COLOR] Neither have I, perhaps a new installation is in order. As I wrote, movies show up as expected.

Edit: seems to be ok here now. I don't know if the OP's drive is being detected or not.

---

### Post by amano on 2017-10-01
Not finding audio cds would be a bummer. I will test tomorrow.

Is there a bug filed already?

---

### Post by mc4man on 2017-10-01
> **Frogs Hair said:**
> Neither have I, perhaps a new installation is in order. As I wrote, movies show up as expected.

Edit: seems to be ok here now. I don't know if the OP's drive is being detected or not.If you then eject the cd & re-insert, does it show up again?

---

### Post by Frogs Hair on 2017-10-01
> **mc4man said:**
> If you then eject the cd & re-insert, does it show up again? Yes, I took four tries before mount indicator showed up properly in the left pane of files. I've had trouble with gvsf before in the development cycle and it could that. Working now though.

---

### Post by corradoventu on 2017-10-02
@mc4man:
- thanks for flagging my bug as confirmed
- audio cds are probably considered 'depreciated' ... may be, but an empty CD or DVD should be detected also if brasero is disappeared 
- If you then eject the cd & re-insert, does it show up again? ... no, also after many tries
- my window for files is much different from the one you attached; why?

---

### Post by mc4man on 2017-10-02
> **corradoventu said:**
> @mc4man:
- thanks for flagging my bug as confirmed
- audio cds are probably considered 'depreciated' ... may be, but an empty CD or DVD should be detected also if brasero is disappeared 
- If you then eject the cd & re-insert, does it show up again? ... no, also after many tries
- my window for files is much different from the one you attached; why?
The reference to depreciated was done facetiously..
Anyway your bug is on lshw which I'm pretty sure isn't the problem. Haven't really come up with what is behind this, maybe some other more 'popular' sources should be added to see what shakes out.

Another example - 
installed brasero, inserted audio cd. Nautilus never shows but brasero, like audacious, can find..

---

### Post by mc4man on 2017-10-02
Found the likely culprit - udisks2
Downgrading to the last version & rebooting, then everything works as expected.
Here used these 3 packages to downgrade,
gir1.2-udisks-2.0_2.1.8-1ubuntu1_amd64.deb
libudisks2-0_2.1.8-1ubuntu1_amd64.deb  
udisks2_2.1.8-1ubuntu1_amd64.deb

Found here [https://launchpad.net/ubuntu/+source/udisks2/2.1.8-1ubuntu1/+build/12375528](https://launchpad.net/ubuntu/+source/udisks2/2.1.8-1ubuntu1/+build/12375528)

If anyone checks & finds working then confirm udisks2 in report. Edit - no need to confirm udisks2, bug has proper attention now..

Also seems latest udisks2, (2.7.3-4),  works fine so expect 18.04 will be ok.

---

