---
title: "Arcserve Client Agent - Anybody managed to install it?"
date: 2010-02-17
forum: Server Platforms
---

### Post by MaximumFish on 2010-02-17
Hi all,

We've just bought four copies of the Arcserve Client Agent for Linux, assuming it would work under Ubuntu seeing as Debian is supported. Unfortunately it doesn't install properly and CA's tech support simply say "We don't support Ubuntu." Awesome.

So, has anybody managed to get the client agent installed at all? I'm happy to be a guinea pig if you have any suggestions!

Here's the somewhat unhelpful install log:

```

Selecting previously deselected package babcmagt.
(Reading database ... 25318 files and directories currently installed.)
Unpacking babcmagt (from .../Agent/Linux/./babcmagt.deb) ...
Setting up babcmagt (11.5.0) ...
[: 108: /opt/CA/BABcmagt/nls/-e/Messages: unexpected operator
[: 71: /opt/CA/BABcmagt/nls/-e/Messages: unexpected operator

Selecting previously deselected package babagntux.
(Reading database ... 25451 files and directories currently installed.)
Unpacking babagntux (from .../Agent/Linux/./babagtux.deb) ...
Setting up babagntux (11.5.0) ...
[: 108: /opt/CA/BABcmagt/nls/-e/Messages: unexpected operator
[: 89: /opt/CA/BABcmagt/nls/-e/Messages: unexpected operator
[: 642: /opt/CA/BABcmagt/nls/-e/Messages: unexpected operator
[: 642: /opt/CA/BABcmagt/nls/-e/Messages: unexpected operator
[: 642: /opt/CA/BABcmagt/nls/-e/Messages: unexpected operator

-e
-e
-e
-e
Congratulations!  The babagntux package has been installed.
You will need to set it up before using by running the
uagentsetup script.

```

Running the uagentsetup script produces similar unexpected operator messages.

You can download a trial ISO of Arcserve for Linux if you'd like to tinker yourself. The client agent can be found in the Agent/Linux directory.

[https://www.ca.com/us/Register/form.aspx?CID=44277](https://www.ca.com/us/Register/form.aspx?CID=44277)

Any and all suggestions very much appreciated!

Max

---

### Post by skijk on 2010-03-11
We are experience similar problems.
Our main fileserver is running Ubuntu and I also assumed the .deb should work (maybe with some tinkering) on ubuntu, but that was not the case.

So consider this thread bumped.

---

### Post by MaximumFish on 2010-03-11
We were eventually forced to switch to Debian due to a lack of any information online and CA's support flat out refusing to "support" Ubuntu.

However, when trying to find information on another problem, I stumbled across this page, which explains how to install the agent manually. Check out the bottom of the page for Ubuntu specific instructions!

[http://kennethdalbjerg.dk/2007/12/14/ca-brightstor-115-under-linux](http://kennethdalbjerg.dk/2007/12/14/ca-brightstor-115-under-linux)

Debian's similar enough to Ubuntu that we haven't gone back, so I haven't tried these instructions myself, but I'd be interested to know if it works for you.

---

### Post by dimothy10 on 2012-02-14
the link worked like a charm.  am using r16 version of Arcserve so a few changes to directory paths but the jist of the guide works wonders!

---

### Post by nothingspecial on 2012-02-14
Please don't bump old threads to the top.

Closed.

---

