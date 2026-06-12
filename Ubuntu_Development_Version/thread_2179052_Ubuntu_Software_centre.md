---
title: "Ubuntu Software centre"
date: 2013-10-06
forum: Ubuntu Development Version
---

### Post by amir_ali2 on 2013-10-06
Hello Sir/Madam...

i am facing problem with Ubuntu Software Centre, i try to launch it but when i click on it, nothing opening.
simply i can't load Ubuntu software centre to install or remove any application. would you please guide and help me how i can load it???

---

### Post by cariboo on 2013-10-07
When you try to start the Software Centre in a terminal, what error message do you get?

---

### Post by amir_ali2 on 2013-10-07
hello there, that's the thing i not get any error or any message, just nothing at all... i do double click it's get busy sign like something is nearly open but nothing at the end. even no error message

---

### Post by santosh83 on 2013-10-07
> **amir_ali2 said:**
> hello there, that's the thing i not get any error or any message, just nothing at all... i do double click it's get busy sign like something is nearly open but nothing at the end. even no error message

Hi caribou suggested you launch Ubuntu Software Center from a terminal emulator so any error message can be spotted. Launching from the menu will not display such messages. Please follow the instructions below and report back on what you see.

Press ALT+F2
Type: 'x-terminal-emulator' (without the quotes) and hit ENTER
In the terminal emulator type the command: 'ubuntu-software-center'

Now if there are any error messages you might get a hint as to what's wrong.

---

### Post by Mateusz Stachowski on 2013-10-07
You can launch terminal in Ubuntu with keyboard shortcut Ctrl+Alt+T. The command that you type in terminal should be 'software-center' or 'software-center-gtk3' because that's the actual binaries names of Ubuntu Software Center.

---

### Post by amir_ali2 on 2013-10-11
Hello Mr. Santosh... i try to follow your instructions as you mention above. that way there error come "command not found".
Mr. Mateusz. i try to follow your instructions aswell dear and that way "No such file or directory".
so is it's mean Software center is not install in my system or deleted??? if this then how i can download that again in free?

---

### Post by sammiev on 2013-10-11
Hi amir_ali2,

You can install Synaptic Package Manager. 

[http://askubuntu.com/questions/131979/how-to-install-synaptic-package-manager](http://askubuntu.com/questions/131979/how-to-install-synaptic-package-manager)

---

### Post by oldos2er on 2013-10-12
> **amir_ali2 said:**
> Hello Mr. Santosh... i try to follow your instructions as you mention above. that way there error come "command not found".
Mr. Mateusz. i try to follow your instructions aswell dear and that way "No such file or directory".
so is it's mean Software center is not install in my system or deleted??? if this then how i can download that again in free?

Which version of Ubuntu are you using?

You can install Software Center with ```
sudo apt-get update && sudo apt-get install software-center
```

---

### Post by amir_ali2 on 2013-10-16
Hello dear Sammiev...

i already have Synaptic Package manager installed in to my system.
but it's showing error on opening "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report"
My Ubuntu Software Center already not working so what other step i can take to install Software center to download softwares in my System. i am using currently "Release 10.04 (lucid) Kernel Linux 2.6.32-33-generic"

---

### Post by slickymaster on 2013-10-16
> **amir_ali2 said:**
> Hello dear Sammiev...

i already have Synaptic Package manager installed in to my system.
but it's showing error on opening "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report"...
Have you tried to do what he is suggesting? Open a terminal window and run```
sudo dpkg --configure -a
```
> **amir_ali2 said:**
> ...i am using currently "Release 10.04 (lucid) Kernel Linux 2.6.32-33-generic"
Unless your using the server edition which will be maintained until April 2015, I would advise you to upgrade your Ubuntu system, because 10.04 desktop edition faced his EOL last May

---

