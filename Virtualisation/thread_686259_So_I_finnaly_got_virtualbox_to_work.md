---
title: "So I finnaly got virtualbox to work"
date: 2008-02-03
forum: Virtualisation
---

### Post by Hmarroqu on 2008-02-03
[IMG]http://lh3.google.com/halexmar6/R6VqnpwjwZI/AAAAAAAAAGA/xlQdC3HTNy4/Screenshot.png?imgmax=720[/IMG]

I have some issues as you can tell by the fullscreen pic i took...

I would really appreciate it if anyone can help.

First, i cant get the fullscreen to be really full screen but thats the least of my worries

I currently have dualboot, one windows partition, a shared FAT32 partition and my ubuntu partition...

You can probably guess Im trying to eliminate dual boot entirely...

How can I access any partition with my virtual machine ?

---

### Post by stalker145 on 2008-02-03
> **Hmarroqu said:**
> I have some issues as you can tell by the fullscreen pic i took...

I would really appreciate it if anyone can help.

First, i cant get the fullscreen to be really full screen but thats the least of my worries

I currently have dualboot, one windows partition, a shared FAT32 partition and my ubuntu partition...

You can probably guess Im trying to eliminate dual boot entirely...

How can I access any partition with my virtual machine ?

Firstly, for the resolution. Have you installed the Guest Addons? It's under Devices ~> Install Guest Additions.

Secondly, for sharing drives, all you need do is under the VM's configuration look for Shared Folders (or something like that) and share the folders of your host you wish.

Check back if this isn't what you were looking for or you have problems.

---

### Post by Hmarroqu on 2008-02-03
> **stalker145 said:**
> Firstly, for the resolution. Have you installed the Guest Addons? It's under Devices ~> Install Guest Additions.

Secondly, for sharing drives, all you need do is under the VM's configuration look for Shared Folders (or something like that) and share the folders of your host you wish.

Check back if this isn't what you were looking for or you have problems.

[IMG]http://lh5.google.com/halexmar6/R6Z5E5wjweI/AAAAAAAAAHA/T8qSX8mjitM/Screenshot.png?imgmax=512[/IMG]
^ that partition is basically what i use between my dual boots, its my shared partition. and nothing shows up in the virtual windows "mycomputer" or anywhere else for that matter. I must have to do something else on top of what i already did....dont know what tho.

I dont know where """Devices ~> Install Guest Additions""" is at....

But i realized that i can get 800x600 an d 1028x768 on the VM so i can just barely use 1028 on my screen...its ok not that bad...but Im sure that is a driver problem with the VM.

---

### Post by stalker145 on 2008-02-04
> **Hmarroqu said:**
> I dont know where """Devices ~> Install Guest Additions""" is at....

Check the attached screen shot. If it doesn't come up with the install dialogue shortly after clicking that menu, find your guest's CD drive and run it from there.

EDIT: Added screen shot and explanation below.

Check under My Network Places ~> Entire Network ~> Virtualbox Shared Folders.

---

### Post by Hmarroqu on 2008-02-04
> **stalker145 said:**
> Check the attached screen shot. If it doesn't come up with the install dialogue shortly after clicking that menu, find your guest's CD drive and run it from there.

EDIT: Added screen shot and explanation below.

Check under My Network Places ~> Entire Network ~> Virtualbox Shared Folders.

Wow thanks very much, I have it fitting perfectly on my screen now!

[IMG]http://lh3.google.com/halexmar6/R6dMvJwjwfI/AAAAAAAAAHI/EdvnIcNIoEM/Screenshot.png?imgmax=640[/IMG]

Its Beautiful seeing that...

Now I just have to find out how to access my HDDs in the virtual machine...then i can die happy.

---

### Post by stalker145 on 2008-02-04
> **Hmarroqu said:**
> Now I just have to find out how to access my HDDs in the virtual machine...then i can die happy.

I don't know if you can do it while the guest is running, but the window that open when you first start VirtualBox is where I make the changes.

Over on the right-hand side you can see where you can make changes to the guest. In there, You will find a "shared folders" area. Just use the top-right button to open the dialogue to make a new share. You should be able to share any folder mounted on your computer.

Also, have you tried the right<ctrl>+l (as in eLL) trick yet? Make it seamless. You lose the background/desktop and are left with just the Windows taskbar and any guest windows you open up. I use it to screw people up when they're looking over my shoulder ;)

I'd post a series of screen shots to help out, but my job is making me actually come in to work... how dare they... LOL Maybe when I get home if you still need it.

---

### Post by Hmarroqu on 2008-02-04
seamless huh...that sounds interesting...I found out btw that I can access my shared drive by not only enabling root and user for virtualusers in groups but i also by enableing the partion in shared folders in ubuntu...so all ths stuff and i finally can access my partition in windows thru Windows Networking.  SO aftre all that stuff, im disapointedly finding out that my virtual machine LAGGS so much when accessing the shared partition. like...Ill play music with itunes using my partitoin library and just by moving the window it skips the song....not only that but it takes 30seconds to access the drive and open files...not cool.

Using 512 mem, 8mb of vid and still no dice...this is only when i access the drive tho. other than that it works flawlessly, better than native...to bad i need it for my itunes and work.

Its funny cause if i work on it, i will be accesing another virtual terminal over at my office since i work at home. virtual machine runnning a virtual machine!

---

### Post by jjsonp on 2008-02-04
I set up 'seamless' last night - very cool. Basically you get the windows taskbar atop the Ubuntu desktop. I set it up like this:

* In the WinXP VM, open the registry editor (Start &#8594; Run &#8594; regedit) and press enter. Navigate to HKEY_CURRENT_ USER &#8594; Software &#8594; Microsoft &#8594; Windows &#8594; Current Version &#8594; Policies &#8594; Explorer. Right-click in the whitespace on the right panel, create a new DWORD entry and name it 'NoDesktop'; set its value to 1.
* Inside the VM, select the top Devices menu and select Install Guest Additions. After the installation is complete, reboot the VM.
* Log back into the VM, select the top Machine menu and select 'Seamless Mode'. To toggle seamless mode via keyboard, press (right) Ctrl+L.

Found those [here]("http://www.itvidya.com/how_to_run_windows_and_linux_at_one_place").

---

