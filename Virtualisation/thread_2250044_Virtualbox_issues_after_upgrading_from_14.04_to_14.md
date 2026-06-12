---
title: "Virtualbox issues after upgrading from 14.04 to 14.10"
date: 2014-10-26
forum: Virtualisation
---

### Post by d-koroliov on 2014-10-26
I have the same problem. Virtualbox just does not start VMs. When I try to start an existing VM or create a new one at first it tries to load Windows but then crashes (a crash occurs when Windows boots). It does not matter whether I try to start windows normally or in the safe mode or load from an install CD. The log does not said anything usefull to me (I tried to find today's date in the log but found nothing)

---

### Post by d-koroliov on 2014-10-26
[ATTACH=CONFIG]257502[/ATTACH]

this is how it looks

---

### Post by ibjsb4 on 2014-10-26
Without error message, this is only guesswork.  Whats your dkms status?
```
dkms status
```
And a curiosity, your screenshot does not show any processors under system.
[ATTACH=CONFIG]257503[/ATTACH]
Edit
Never mind, one processor will not show.

---

### Post by d-koroliov on 2014-10-26
this is the output
$ dkms status 
virtualbox, 4.3.18, 3.13.0-37-generic, x86_64: installed
virtualbox, 4.3.18, 3.16.0-23-generic, x86_64: installed

---

### Post by overdrank on 2014-10-26
> **d-koroliov said:**
> I have the same problem. Virtualbox just does not start VMs. When I try to start an existing VM or create a new one at first it tries to load Windows but then crashes (a crash occurs when Windows boots). It does not matter whether I try to start windows normally or in the safe mode or load from an install CD. The log does not said anything usefull to me (I tried to find today's date in the log but found nothing)

Hi and welcome, I have moved your post to it's own thread as to not hijack other's thread.

---

### Post by ibjsb4 on 2014-10-26
> **overdrank said:**
> Hi and welcome, I have moved your post to it's own thread as to not hijack other's thread.
I missed that :rolleyes:
Be back after the game(s).

---

### Post by d-koroliov on 2014-10-27
Fixed. The problem was in the extention pack for the older Virtualbox verion. After it's removal everything works normally

---

### Post by open2linux on 2014-10-27
I have exactly the same problem you had, happy that you managed to solve it.
Can you elaborate a little more explaining how did it?
That may help others with the same isse. Certainlly it will help me.
Thanks!

---

### Post by d-koroliov on 2014-10-27
ok, let's explain this a bit more.

The problem was that I installed Virtualbox extension pack previously and forgot about this. On update for some reason the old extension pack (for the previous verion of Virtualbox) was not removed automatically. And that is why I was not able to start any of my VMs. To solve this one needs to remove an old extention pack (and may be install a new one), this can be done in the file->preferences->extensions menu (or just press Ctrl+G and select the "extensions" tab). After that if one will not install a new version of the extension pack then it might be necessary to disable some USB controllers etc. for a particular VM (this is not going to be a problem, because Virtualbox errors messages in these cases are pretty clear).

Below is a screenshot to show where to remove (and install) an extension pack.

[ATTACH=CONFIG]257528[/ATTACH]

---

### Post by thomas-toem on 2014-10-28
I had the same,
in my case the fix was to disable 2d/3d.
#
thomas

---

### Post by open2linux on 2014-11-01
Thanks d-koroliov and thomas-toem for your help. But still I can not make virtualbox works.
Windows7 begins the starting process but it aborts and goes back to the virtualbox main screen.
I get this error message:

-----------------------------
There is no virtual machine with the identifier f4a630af-29ae-401f-8968-48f687a51d70.
Could not find a registered machine with UUID {f4a630af-29ae-401f-8968-48f687a51d70}.
Result Code: 
VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)
Component: 
VirtualBox
Interface: 
IVirtualBox {fafa4e17-1ee2-4905-a10e-fe7c18bf5554}[ATTACH=CONFIG]257679[/ATTACH][ATTACH=CONFIG]257680[/ATTACH][ATTACH=CONFIG]257681[/ATTACH][ATTACH=CONFIG]257679[/ATTACH][ATTACH=CONFIG]257680[/ATTACH][ATTACH=CONFIG]257681[/ATTACH]

-------------------
And in the settings page it doesn apperas any Extensions.
Enclosed the screenshots.
(I don know why the duplicated images, sorry for that)

---

### Post by impliedconsent2 on 2014-11-02
> **d-koroliov said:**
> To solve this one needs to remove an old extension pack (and may be install a new one), this can be done in the **file->preferences->extensions** menu (or just press Ctrl+G and select the "extensions" tab).

Just download the [extension pack]("https://www.virtualbox.org/wiki/Downloads") and add it. It will automatically upgrade the old version to the new version.

---

### Post by open2linux on 2014-11-03
Solved.
After removing an old extension pack and I disabling the usb controller it works.
Thanks!

---

### Post by slickymaster on 2014-11-03
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by Joakim_Lindbom on 2015-04-13
Removing the ExtPack (and reinstalling VirtualBox) didn't do the trick - but a variation did:

sudo VBoxManage extpack uninstall "Oracle VM VirtualBox Extension Pack"
wget [http://dlc-cdn.sun.com/virtualbox/4.3.18/Oracle_VM_VirtualBox_Extension_Pack-4.3.18-96516.vbox-extpack]("http://dlc-cdn.sun.com/virtualbox/4.3.18/Oracle_VM_VirtualBox_Extension_Pack-4.3.18-96516.vbox-extpacksudo") 
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-4.3.18-96516.vbox-extpack 

Now all seems to be working fine.

---

### Post by lukastojanovicbg on 2015-11-27
Thanks! You saved my day.

---

