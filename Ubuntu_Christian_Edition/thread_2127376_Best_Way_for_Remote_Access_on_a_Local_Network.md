---
title: "Best Way for Remote Access on a Local Network?"
date: 2013-03-19
forum: Ubuntu Christian Edition
---

### Post by parkernathan on 2013-03-19
What's the easiest way to setup machines on a local network so I can remotely access them and see the computer screen (while on the local network, not from afar off)? That way I could configure DansGuardian and tweak settings from my desk instead of having to go down the hall and physically sit at the machine when I need to tweak settings. 

Thanks!

---

### Post by SeijiSensei on 2013-03-19
Install [openssh-server]("https://help.ubuntu.com/community/SSH") on the remote machines.

---

### Post by papibe on 2013-03-20
Hi parkernathan.

If you want to see the screen, as you were sitting in front of the computer, there are several options.

The simplest is to use what is preinstalled on Ubuntu.

On 12.04:
[LIST]
[*]Enable remote access by opening 'Desktop Sharing'.
[*]Then on the client, open 'Remote Desktop Client'
[/LIST]
On 10.04:
[LIST]
[*]Enable remote access by opening 'Remote Desktop'.
[*]Then on the client, open 'Remote Desktop Viewer'.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by parkernathan on 2013-03-20
OK perfect! Once I setup a couple of Ubuntu machines, I'll give it a spin and post my details here. Thanks a bunch for your assistance!

---

