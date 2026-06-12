---
title: "Lightweight way to use GUI tools without a desktop environment"
date: 2017-01-07
forum: Virtualisation
---

### Post by horsebox2 on 2017-01-07
I'm running a Ubuntu server in VirtualBox, and in some cases it would be so much easier to use gedit to edit config files than using vim or nano. Rather than installing a whole desktop environment like Unity, is there a way to install just a simple system to enable you to launch GUI tools like gedit?

---

### Post by DuckHook on 2017-01-07
As the name suggests, *gedit* is a gnome tool and will drag in a *ton* of dependencies which will basically amount to installing the Unity Desktop. You probably want to go about it the other way: install a *really* lightweight window environment and just make use of its native editor. Something like LXDE is still a DE, but a very light one. Its native GUI editor is *leafpad*. Not as full-featured as gedit, but it doesn't need the python/gir stack.

Another option is to go for a window manager environment like Bodhi, though the resource savings over LXDE are marginal.

Most resource efficient is running a GUI editor in a simple xwindow environment, but that is very awkward and you would probably prefer *nano* at that point.

Last but not least (and I do understand that you didn't ask for this input), the lightest GUI environment is still multiple times the resource-hog that is the server CLI environment. It is also multiple times the attack surface and therefore, commensurately more insecure. While the initial learning curve for CLI-based editors is rather steep, the eventual mastery of such tools makes the GUI superfluous. In return, your server will be faster and more secure for it.

---

### Post by DuckHook on 2017-01-07
Further thoughts:

There is really nothing magical about the word "server". A server is simply an appliance that hosts some service to one or more clients. Therefore, if you must have a GUI, then it makes sense to simply install Lubuntu into your VM and add the server components in the usual way using apt or the software centre or whichever installation method you are most comfortable with.

The "server" image that Ubuntu offers is actually a shorthand for powerusers who *don't want a GUI*. It should really read "CLI" image. Yes, there are a few tweaks that make it run more efficiently as a server, but these are rather unimportant and certainly won't make a difference to you if you are running it in a VM anyway. By installing any GUI component, you are basically breaking its "server" status and may as well start with a GUI DE. Much less painful that way.

---

### Post by Habitual on 2017-01-09
Remote edit via Filezilla if you must insist on a GUI for editing.

---

### Post by DuckHook on 2017-01-09
> **Habitual said:**
> Remote edit via Filezilla if you must insist on a GUI for editing.+1

This is a very creative workaround.

@OP

While Habitual's solution is ingenious, and avoids all the pitfalls associated with dragging in a DE, it does have a few caveats that you should be aware of:

[LIST=1]
[*]You must open your server to FTP, SFTP or FTPS, which is a security exposure. FTP in particular is a notorious and easily exploited security hole.
[*]The usual security practice with any of the above protocols is to limit their access to a well-sandboxed partition. However, your stated intent is to edit config files, which means that you will have to allow access to your root filesystem. Thar be dragons.
[/LIST]
Still, if your VM is not exposed to the big bad internet but constrained within your own LAN which is adequately firewalled, the various security exposures may be no big deal to you. You will have to learn how to install and configure SFTP/FTPS (I strongly urge against installing FTP if only for the cultivation of good habits alone), but this is a once-over thing.

If you decide against Habitual's method and prefer a simple DE instead, then seeing as how you are currently running the server edition, there is no need to reinstall anything. Just run:```
sudo tasksel
```…and select an appropriate desktop choice. Tasksel also allows you to install bundles of services that are common server requirements. Since your stated intent is still to run as lean a server environment as possible, I would recommend Lubuntu minimal or Xubuntu minimal. Their default editor should already be part of a minimal install. If not, you can install Leafpad or Mousepad respectively.

---

### Post by DuckHook on 2017-01-09
In the spirit of Habitual's innovative solutions :)

…you may find that the following measures give you enough "graphical" capabilities that you can forego both a GUI and a workaround like Filezilla.

[LIST=1]
[*]Install *gpm*. This is a driver that provides mouse support within a CLI environment.
[*]Install *mc*. *Midnight Commander* is a slick piece of work in its own right and, in my opinion, is indispensible for file manipulation, especially for users new to the CLI.
[*]In your case, its real value is its editor, *mcedit*. Unlike *nano*, *mcedit* is more mouse-aware, with drop-down menus, though no drag-and-drop. It requires *gpm* to provide the mouse capabilities. *gpm* works with highlighting in *nano* too, but since *nano* has no drop-down menus, it isn't as comforting to new users.
[*]Various commands like cut, copy and paste differ from the usual GUI equivalents, but they are easy enough to re-learn and are a small price to pay for an almost-GUI-like experience.
[*]Note that if operating *gpm* from within a VM on a GUI host, the guest mouse will sometimes desynchronize from the host mouse. You need to decouple mouse integration and isolate the guest mouse from the host in order to avoid this.
[/LIST]

---

### Post by bearlake on 2017-01-09
I have tried using mc installed on the server and running it from the client.

From the client, you can use the mouse with mc without adding any other software.

Makes it great for reviewing all the logs and editing files.

If you have nautilus installed on the client you can transfer files to and from the server with 2 mouse clicks.

There is a lot of good programs listed in this thread that just work. :)

---

### Post by DuckHook on 2017-01-09
> **bearlake said:**
> …using mc installed on the server and running it from the client.

From the client, you can use the mouse with mc without adding any other software.

Makes it great for reviewing all the logs and editing files…Yet another excellent suggestion.

@OP

I believe what bearlake is referring to is accessing your VM through SSH using Ubuntu's Terminal. Firstly, SSH is a far more secure protocol than FTP. Secondly, by SSH-ing into your VM using a graphical app like Terminal, you leverage its built-in graphical capabilities to allow the mouse in your client to do things like access drop-down menus, etc. You would still need *mc* and *mcedit*. Apps (like *nano*) do not magically gain graphical abilities just because they are being controlled through a GUI terminal, but graphics-aware apps like *mc*, *mcedit* or *htop* gain a certain amount of mouse functionality.

This method requires you to install *openssh-server* in your VM. You would then access the VM through an SSH connection using Terminal instead of working on the remote desktop native to most VMs. It has the added advantage that your VM could be running on a remote machine and you could still access it.

You now have more than enough suggestions to choose one that works for you.

Let us know how it goes.

---

### Post by bearlake on 2017-01-09
> **DuckHook said:**
> Yet another excellent suggestion.

@OP

I believe what bearlake is referring to is accessing your VM through SSH using Ubuntu's Terminal.

You now have more than enough suggestions to choose one that works for you.

Let us know how it goes.

Correct you are. :)

---

### Post by KillerKelvUK on 2017-01-12
Wow loving mc and mcedit, not heard of them until this thread, always just ssh'd to my vm's and used cli with nano.

Thanks guys, good and useful thread!

=d>

---

### Post by sudodus on 2017-01-12
When you talk about ***mc*** (Midnight Commander) I remember ***nc*** (Norton Commander), that I used in MSDOS. It is nice that this tool lives as FOSS :-)

---

### Post by DuckHook on 2017-01-12
> **sudodus said:**
> When you talk about ***mc*** (Midnight Commander) I remember ***nc*** (Norton Commander), that I used in MSDOS. It is nice that this tool lives as FOSS :-)You realize how much this dates us, right? :lolflag:

---

### Post by geeksmith on 2017-01-12
Similar to using FileZilla, you can use sshfs to mount your server filesystem locally and edit files with your preferred editor.

When I first started using Linux, I chose to learn vi because
1. I knew it would be on nearly every *nix system I'd ever use
2. It's very flexible and powerful
3. It freed me from needing a desktop environment for simple file edits

I'd suggest learning vi or emacs -- both are great tools to have in your belt.

---

