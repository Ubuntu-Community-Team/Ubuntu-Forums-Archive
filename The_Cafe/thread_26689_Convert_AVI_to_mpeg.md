---
title: "Convert AVI to mpeg"
date: 2005-04-13
forum: The Cafe
---

### Post by steffen on 2005-04-13
Anyone know a good software (prefereably in Ubuntu repos) that can convert my  DivX and Xvids to mpeg, so I can burn them to VCD with K3B?

I've been looking at tovid.sourceforge.net, but its not in repository. It will be an option if there's none...

---

### Post by gil-galad on 2005-04-13
Avidemux is a pretty good one.  Not in the official repositories though.

---

### Post by steffen on 2005-04-13
Looks promising. I see it's in Marillat. Can't install it because of dependancies ;(

---

### Post by robertmf on 2007-12-31
> **steffen said:**
> Anyone know a good software (prefereably in Ubuntu repos) that can convert my  DivX and Xvids to mpeg, so I can burn them to VCD with K3B?

I've been looking at tovid.sourceforge.net, but its not in repository. It will be an option if there's none...
[COLOR="DarkRed"]
Make sure you have all tovid dependencies satisfied :-P  

I've been having success with tovid cli.  Add your videos and then [save to a script].  Then, edit out the menu and run.   Using the tovid cli you also have access to the cli options such as using -ffmpeg and -fit  to a discsize.

You can also use mkisofs, growisofs -Z, and makedvd on the tovid -o mpg to burn to disc

mjpegtools is another option for encoding but with a (for me) difficult install.

I have not had any success with devede
.[/COLOR]

---

### Post by bubwitmaingay on 2009-02-09
If you cannot install the repo because of dependency issues try the terminal, by simply typing:

```
sudo apt-get install avidemux
```

...and the terminal will install everything, and will find the dependencies for you.

I hope that works. Thanks.

I always use the terminal whenever there is a repository dependency issue. The only thing is that you have to know the name of the application (since sometimes it is different from what you have known).

---

