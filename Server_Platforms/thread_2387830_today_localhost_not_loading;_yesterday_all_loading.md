---
title: "today localhost not loading; yesterday all loading fine"
date: 2018-03-24
forum: Server Platforms
---

### Post by nickdc on 2018-03-24
After some updates to the code of a small website it was working flawlessly in a testbed on my UbuntuGnome 16.04 desktop, running the lamp server with php5.6 installed as suggested here: [https://gist.github.com/ericfledderman/6c4f0f7e6ffa3477372ebf5392bad6cd](https://gist.github.com/ericfledderman/6c4f0f7e6ffa3477372ebf5392bad6cd) To get it working, guided by the coder who updated the site, I had to edit the apache2.conf file, changing all instances of <AllowOverride None> to <AllowOverride All>. After that tweak the site worked perfectly when entering "localhost" in Firefox. But today Firefox simply displays a pane: "You have chosen to open:  which is: application/x-httpd-ea-php56 (1.3 kB)  from: [http://localhost](http://localhost)  What should Firefox do with this file? " etc   This is what happened when I first tried to run the test site, stupidly forgetting that I needed to install the server packages first (:redface:). But after installing the lamp server with php5.6 everything loaded fine. Why on earth has it stopped working now?

I can't be 100% certain, but I think I did a standard system update yesterday - could that have changed something?  I'm pretty sure I didn't make any changes to the server configuration - after all, it was working perfectly.

How do I troubleshoot this?

PS I've just discovered that if in the browser address bar I enter the local IP address for the pc holding the local server (instead of "localhost") the site loads as usual, so perhaps not as big a problem as I'd thought. But why doesn't "localhost" work anymore?

---

### Post by nickdc on 2018-03-24
All working again now - weird! Maybe a browser caching issue? - though I didn't consciously clear the cache.

---

