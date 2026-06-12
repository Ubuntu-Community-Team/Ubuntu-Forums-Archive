---
title: "wine with executable odd problem"
date: 2010-07-24
forum: Wine
---

### Post by Ceballo on 2010-07-24
OK so I use wine for most window programs and I haven't had a problem with it up until now. Every time I want to run an executable that does NOT involve you to install it, it never runs. But when I try running an executable that's an installation setup it runs and it installs the program fine and runs it fine.

But I really need this program and it doesn't require a setup but wine refuses to open/run it. What could the problem be?

---

### Post by Bertus_Nel on 2010-07-24
I had the same problem with Drugwars for windows - I added the app to Wine's config and added the required libraries - I also dropped the exe on the C:\  - that seemed to resolve my issue with that one application. 

Not to sure if the app creates like a temp file - and on Linux the program doesnt see the default path to your temp folder.

Hope this info will be of some value.;)

---

### Post by asdfoo on 2010-07-24
your post is lacking any useful information

a) which version of wine are you using? open a terminal and type `wine --version`
b) what is the name of the application you are trying to run?
c) where is the application located? if it's on your windows partition, then you should not be running it from there.
d) provide terminal output including the command you used to start it

---

