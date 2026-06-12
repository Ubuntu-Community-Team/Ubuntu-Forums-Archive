---
title: "New Version of Snort 2.8.0.1 Causing Problems with Snort 2.6/Gutsy/Oinkmaster"
date: 2007-12-01
forum: Server Platforms
---

### Post by eric_stewart on 2007-12-01
I'm posting this since I'm guessing that others that have installed Oinkmaster on their Gutsy or Feisty Fawn Ubuntu boxes will run into the same problem.  In fact it's possible that Snort's not even running on your device and here's why...

Sourcefire recently released version 2.8.0.1 of Snort.  Great news, but unfortunately, if you're using Oinkmaster to download/compare/merge new rules automatically you might be inadvertently sabotaging your Snort installation.  The new version of Snort uses a new rules structure which is incompatible with version 2.6 from the Ubuntu repositories.  I have a post here describing the issue and its resolution more fully.

[http://www.breezy.ca/?q=node/247](http://www.breezy.ca/?q=node/247)

/Eric

---

