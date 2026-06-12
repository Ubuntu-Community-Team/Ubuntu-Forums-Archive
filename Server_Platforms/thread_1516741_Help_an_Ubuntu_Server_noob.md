---
title: "Help an Ubuntu Server noob"
date: 2010-06-24
forum: Server Platforms
---

### Post by TheAlien on 2010-06-24
The only thing I miss with Ubuntu Server, as a freshman, is the ability to copy and paste between VIM and the shells. Like you've got a long command written down in a text file, and then copy and paste that command from VIM and to another terminal session. And vice versa of course. Is this even possible without installing any software?

I would also like to copy and paste between w3m and the shell, and also VIM for that matter.

I don't want to install a GUI, but it takes so much time only writing commands. It would be so much more efficient and practical to be able to copy and paste text all over and between terminals and applications.

Thanks for help!

---

### Post by Ryan Dwyer on 2010-06-24
If you connect via SSH from a machine with a GUI you can copy and paste anything displayed in the terminal using Ctrl + Shift + C and Ctrl + Shift + V.

---

### Post by TheAlien on 2010-06-24
> **Ryan Dwyer said:**
> If you connect via SSH from a machine with a GUI you can copy and paste anything displayed in the terminal using Ctrl + Shift + C and Ctrl + Shift + V.

I don't have that option.

Is this the only way?

---

### Post by abraxas334 on 2010-06-24
Does highlighting and pressing middle mouse button work? I think it works for me.

---

### Post by Yarui on 2010-06-24
I'm a little unsure what your exact setup is.  You said you want to copy from one terminal to another but then a little later you say you don't want to install a GUI.  I always thought terminal was a name specifically used for the GUI shell emulator, if you don't have a GUI installed what do you mean by copying from one terminal to another?

If the way you used to do it was through ssh, that may be where the copy and paste functions came from.  That may have been a function of the ssh client, not the OS.  If there is no built in way to copy and paste in the shell, and I have never known of one, then your only choice is probably to install something that adds the functionality.  I believe key bindings are entirely managed by your desktop management system, though.

If you want to leave your ubuntu machine entirely command line based, but have another computer with a desktop OS installed, your best bet may be to install an ssh server on the ubuntu machine and then use the other computer to ssh into the ubuntu machine.  If the copy and paste functions did come from your ssh client then this will probably solve your problem, if it is an acceptable solution.

---

### Post by Jaysundahl on 2010-06-24
It looks like GNU screen will do what you want, it seems to be installed by default in the desktop edition and works fine in a Crtl-alt-F1 terminal session. You'll have to learn its command set though. I don't have a server install to verify it on and haven't worked through the copy and paste stuff either.

---

### Post by TheAlien on 2010-06-25
Thanks for your suggestions.

I have a text file that I open in vim (tty1) that contains a lot of long commands. So it would've been more efficient for me to be able to copy those commands to a different shell (tty2) rather than reading them and then write them by hand. I would also like to copy text from w3m and paste it into wherever I like.

But obviously this isn't going to happen by using Ubuntu Server straight out of the box, something that I want to do anyway. So I'm just writing everything by hand, even though it takes a lot longer time.

---

### Post by clrg on 2010-06-25
If you use the same commands frequently, use aliases.
For example
```
alias ll="ls -lah"
```
or
```
alias cfstab="cat /etc/fstab"
```
and
```
alias srv="ssh -l user -A -p 1234 server.domain.tld"
```

You get the idea. If a command is too complex for an alias or needs very specific options, write a script you can pass those options to.

---

### Post by koenn on 2010-06-25
+1 for aliases


I doubt you can copy between TTYs, as the represent separate sessions.

If you have a mouse driver installed, any text on your screen that you highlite, can be copied and pasted with a single middle-click (3-button-mouse) so any program that gets the desired text on your screen (grep, less, more, cat, vim, ...) would let you do this.


You can start a shell from within vim (:!) but I don't know if that would be of any help to get a line from the file executed. It might be a step in the right direction.  It'll work with the :! + middle-click copy/paste, but I'm not sure about 'keyboard only' commands


screen is also worth looking into, especially if you want to do this 'keyboard only'

---

### Post by clrg on 2010-06-25
I'm an idiot! Of course there is a better solution (I know this from HP-UNIX, actually :> )

Type 
```
set -o vi
```
in your bash shell, which will activate the vi mode. Now you can use your shell as in vi.

For example, esc-esc-k will take you to the last command. 
Or esc-esc-16x will delete 16 characters on the current line.
Esc-esc-2cw will replace two words on the current line.

Also, you can use cut/copy and paste in the shell as you would in vi.

Hope this helps!

---

