---
title: "Landscape issues"
date: 2019-07-10
forum: Ubuntu Cloud and Juju
---

### Post by robcallaway on 2019-07-10
I don't know if this is the correct forum but I didn't see anything specifically outlining Landscape support anywhere else. I have a Landscape server setup, I was able to join a client to it but now I'm trying to get repositories to work. I am going off [https://landscape.canonical.com/static/doc/user-guide/ch09.html](https://landscape.canonical.com/static/doc/user-guide/ch09.html)  And these are the commands it says to run:


gpg --edit-key KEYID gpg --export-secret-keys -a KEYID > secret-key.pemlandscape-api import-gpg-key secret-key secret-key.pem

But when I run the first command it says KEYID not found. When I run the second command it reads "gpg: WARNING: Nothing exported". I am at a loss as to what its actually doing here, am I supposed to get the GPG key from Ubuntu, am I supposed to have my own GPG key server stood up in order to use repositories with Landscape?

---

### Post by james.w.krych on 2019-07-17
Here are some of my notes:
[LEFT][FONT=Arial]apt-get install rng-tools && sudo rngd -r /dev/urandom
[/FONT][FONT=Arial]gpg &#8211;gen-key
[/FONT][FONT=Arial]gpg -K[/FONT]
[FONT=Arial]gpg -a --export-secret-keys 589FC5454E50D88B14AEEEA634FC4E2A24F7E41D  > mirror-key.asc

[/FONT]
[FONT=Arial]**export LANDSCAPE_API_URI="https://landscapetest/api/"**[/FONT][/LEFT]
[FONT=Arial]**export LANDSCAPE_API_KEY="SHB0OELRFXKZ0LLV2818"**[/FONT]
[FONT=Arial][B]export LANDSCAPE_API_SECRET="6IK0yf0Df0tsT6nWurNwdamzmQyZKMxckO2QZvgY"


[/B][/FONT][LEFT][FONT=Arial]landscape-api import-gpg-key mirror-key mirror-key.asc[/FONT]
[/LEFT]
[COLOR=#242729][FONT=Arial][FONT=Arial]landscape-api create-distribution ubuntu[/FONT][/FONT][/COLOR]

[COLOR=#111111][FONT=monospace]landscape-api create-series [COLOR=#183691]\[/COLOR][/FONT][/COLOR]
[COLOR=#111111]  [FONT=monospace]--pockets release,updates,security [/FONT][COLOR=#183691][FONT=monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace]--components main,restricted,universe,multiverse [/FONT][COLOR=#183691][FONT=monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace]--architectures amd64,i386 [/FONT][COLOR=#183691][FONT=monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace]--gpg-key mirror-key [/FONT][COLOR=#183691][FONT=monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace]--mirror-uri http://[/FONT][FONT=monospace]us.[/FONT][FONT=monospace]archive.ubuntu.com/ubuntu/ [/FONT][COLOR=#183691][FONT=monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace]--mirror-series bionic bionic ubuntu 

[/FONT][/COLOR]**[COLOR=#111111][FONT=Arial][B]Sync pockets**[/FONT][/COLOR][/B]

[LEFT][COLOR=#111111][FONT=Arial]**We can sync only one pocket at a time. Once one pocket sync is done, we can start the next one. This command will start the actual mirroring process for the **[/FONT][/COLOR][COLOR=#111111][FONT=Arial]**release**[/FONT][/COLOR][COLOR=#111111][FONT=Arial]** pocket:**[/FONT][/COLOR]

[/LEFT]
[COLOR=#242729][FONT=Consolas][FONT=Arial]landscape-api sync-mirror-pocket release [/FONT][/FONT][/COLOR][COLOR=#242729][COLOR=#242729][FONT=Consolas]bionic[/FONT][/COLOR][COLOR=#242729][FONT=Consolas] ubuntu[/FONT][/COLOR][/COLOR]
[COLOR=#242729][FONT=Consolas][FONT=Arial]landscape-api sync-mirror-pocket updates bionic ubuntu[/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Consolas][FONT=Arial]landscape-api sync-mirror-pocket [/FONT][/FONT][/COLOR][COLOR=#242729][COLOR=#242729][FONT=Consolas]security[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]bionic [/FONT][/COLOR][COLOR=#242729][FONT=Consolas]ubuntu[/FONT][/COLOR][/COLOR]


[COLOR=#242729][FONT=Consolas][FONT=Arial]To check the status, use this with an ID +1[/FONT][/FONT][/COLOR]

[COLOR=#111111][FONT=monospace][FONT=Arial]landscape-api get-activities --query id:[/FONT][/FONT][/COLOR]

[COLOR=#111111][FONT=Ubuntu][FONT=Arial]Packages will be downloaded under the [/FONT][/FONT][/COLOR][COLOR=#111111][COLOR=#111111][FONT=Ubuntu Mono]/var/lib/landscape/landscape-repository/standalone/[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]directory.[/FONT][/COLOR][/COLOR]
[LEFT][COLOR=#111111][FONT=Ubuntu][FONT=Arial]The repositories are also visible via a web browser at: [/FONT][/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu Mono]http://your-server.com/repository/standalone/ubuntu/pool/[/FONT][/COLOR][/LEFT]
[COLOR=#111111][FONT=Ubuntu]and[/FONT][/COLOR]
[LEFT][COLOR=#111111][FONT=Ubuntu Mono]http://your-server.com/repository/standalone/ubuntu/dists/

[/FONT][/COLOR][FONT=Arial]To remove an &#8220;oops&#8221;[/FONT][COLOR=#242729][FONT=Arial][FONT=Arial]landscape-apiremove-series bionic ubuntu[/FONT][/FONT][/COLOR][/LEFT]

---

### Post by deadflowr on 2019-07-17
*Thread moved to **Ubuntu Cloud and Juju***
Per the Ubuntu Cloud and Juju strapline:
> (For questions about Ubuntu Cloud Infrastructure, MAAS, Landscape, and Juju projects in Ubuntu. This also covers traditional use of Ubuntu Server.)

---

### Post by james.w.krych on 2019-08-14
Any change?

---

