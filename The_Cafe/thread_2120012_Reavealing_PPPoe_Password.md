---
title: "Reavealing PPPoe Password?"
date: 2013-02-25
forum: The Cafe
---

### Post by mamamia88 on 2013-02-25
Ok here's the deal.  I want to reset my network.   I use dsl which uses a pppoe authentication.   I know what my username is but it uses a different password.  It's on the configuration page but has astericks covering the password.  Anybody know how to reveal it?   Really want to avoid calling att because i hate dealing with them. I already tried the show password add on for firefox

---

### Post by stinkeye on 2013-02-25
If it's a firefox saved password it can be viewed in edit > preferences > security > saved passwords.

In opera I use this method.
Hit the login button to the the site and quickly hit the reload/stop button before the page redirects 
so you have the asterisks in the password box.
If the asterisks are already visible just go straight to the next step.

Open opera dragonfly... menu > page > developer tools.
Left click in the password box to highlight and then in dragonfly under the properties tab
scroll to the bottom to the **validity** heading.
Directly underneath will be a value showing the password.

---

### Post by mamamia88 on 2013-02-25
validity still displays asterics

---

### Post by stinkeye on 2013-02-25
Don't know then.
Is it a saved firefox password.
Can you login automatically?

---

### Post by mamamia88 on 2013-02-25
> **stinkeye said:**
> Don't know then.
Is it a saved firefox password.
Can you login automatically?

weird i was so worried about needing the password but decided to try and reset anyway.  i just provided my email password then it told me what the pppoe password was.  guess i didn't need to get so technical.  now if i could just figure out why dd-wrt page won't load even though i'm following the directions here [http://www.dd-wrt.com/wiki/index.php/Client_Bridge](http://www.dd-wrt.com/wiki/index.php/Client_Bridge) and know damn well that i set my main router to 192.168.1.1

---

