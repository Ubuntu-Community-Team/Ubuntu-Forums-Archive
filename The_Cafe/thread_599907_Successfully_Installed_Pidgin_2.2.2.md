---
title: "Successfully Installed Pidgin 2.2.2"
date: 2007-11-01
forum: The Cafe
---

### Post by dswhite85 on 2007-11-01
Since Pidgin 2.2.2 came out, there is only one way to get it: Download the Source Code from the Pidgin website ([http://www.pidgin.im/download/]("http://www.pidgin.im/download/")).

To install the Source Code, use either of these guides:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

Once the Source Code is downloaded, right click the file, then use "Extract Here" 
To make sure you can compile the file, get "build-essential" from Synaptic. 
Next open up the terminal and type "sudo apt-get build-dep pidgin" to make sure you get the dependencies needed to compile.
Make sure the terminal is in the directory where you extracted the source code. (Help with navigating the Terminal: [http://monkeyblog.org/ubuntu/installing/#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing/#navigating_the_terminal")).
Once you're in the correct directory, type "./configure"
Next type "make"
Finally, type "sudo make install"
To remove temporary files type "make clean"

Hope that helps for anyone. It all worked very well for myself (First time ever compiling in Linux!). As always, read the README and INSTALL files with the Source Code for further help and information.

---

### Post by cookieofdoom on 2007-11-01
Always happy to see a new release. This version's changelog only shows "Various bug and memory leak fixes". I'll probably wait until it gets added to the repos since I've not had any problems.

Oh, and I might be wrong but I think it's "./configure" not "./compile". :)

---

### Post by bruce89 on 2007-11-01
Pidgin 2.2.2 will appear in my PPA once I can be bothered or it is in Hardy.

---

### Post by dswhite85 on 2007-11-01
> **cookieofdoom said:**
> Always happy to see a new release. This version's changelog only shows "Various bug and memory leak fixes". I'll probably wait until it gets added to the repos since I've not had any problems.

Oh, and I might be wrong but I think it's "./configure" not "./compile". :)

Thanks for the correction! Updated it just now. If you are not experiencing any problems, then no need to upgrade as it fixes mainly bugs. But as for me I like always being up-to-date!:)

---

### Post by Kosimo on 2007-11-01
Is compiling right now. The question is:
Do I have to save that folder in order to uninstall it if I want to?

---

### Post by undine on 2007-11-01
> **Kosimo said:**
> Is compiling right now. The question is:
Do I have to save that folder in order to uninstall it if I want to?

Use checkinstall instead, then you can always remove it later via apt.

I'm not going to install it at this time because I am so happy with 2.2.1 that I don't really see a need. It's not often that I can say that about an application.

---

