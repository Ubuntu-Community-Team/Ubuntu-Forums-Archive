---
title: "[unity] google chrome app shortcut on the bar?"
date: 2010-10-16
forum: Ubuntu Moblin Remix
---

### Post by niewolno on 2010-10-16
I'm using google chrome (chromium from the repos, btw: how do you change the horrible blue icon back to the clasical chrome icon?) and I wanted to add a gmail application shortcut to the unity bar. I created the app shortcut with chrome, it landed in my menu, I clicked on it and... it joined the chrome group on the unity bar. this way I can't add an icon, can I? I just want a button to open my gmail directly, using chrome, that's it.
How do you do that?

I forgot - I'm using UNR 10.10

---

### Post by gyussz on 2010-10-16
> **niewolno said:**
>  btw: how do you change the horrible blue icon back to the clasical chrome icon?)

Chromium from the basic repository is basically not Google Chrome, it's somehow different. If you want to use Google Chrome install it from here: [http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel), the deb installer will add Google Chrome repository to the software channels.

---

### Post by niewolno on 2010-10-16
thanks a lot for the answer. I installed google chrome but apparently chrome (unlike chromium) does *NOT* have the 'keep in launcher' option. Oh well.

And still, I've no idea how to separate chrome/chromium and gmail app shortcut, in order to place two items on the launcher bar. It really wasn't a problem with the 10.4 launcher.

I find the decision to include unity a bit hurried, it seems it's not ready yet.

---

### Post by niewolno on 2010-10-17
installing libunity-dev helps with adding the chrome launcher.

as to the web-app problem, there is a half-way solution:

unity -b [http://any_web_adress.com](http://any_web_adress.com) creates a web app launcher. but it does not work. at least there is a bug:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/660157](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/660157)


then there's another solution, which I found here:

[http://askubuntu.com/questions/4304/how-do-i-put-web-applications-in-my-unity-launcher/4307](http://askubuntu.com/questions/4304/how-do-i-put-web-applications-in-my-unity-launcher/4307)

apparently, as for now there is no easy and definite way of solving the problem.

---

### Post by Joshwaa on 2010-10-17
The Google version of Chrome can be downloaded from [here]("http://www.google.com/chrome"), just click the version you need and download it (Chrome does have multiple Linux versions, thankfully!)

---

