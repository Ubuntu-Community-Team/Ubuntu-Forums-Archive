---
title: "interactive prompt during preseed install?"
date: 2012-04-30
forum: Server Platforms
---

### Post by rgcosma on 2012-04-30
Hello,
At some point during the installation, when target is mounted, I want to prompt the user for one or more strings and use them to generate a bunch of config options. I've tried all kinds of tricks with bash's read and dialog in d-i preseed/late_command, but the installer stubbornly refuses to show a prompt, even if I prefix with exec > anothertty and chvt
Some reading through the debian installer docs shows some very convoluted ways to interact with debconf and not a single actually working example.
Has anyone actually succeeded in adding a custom dialog? I'm guessing it's not rocket science, but debugging is a bitch as the installer is very unforgiving with any syntax errors, the shell is limited (not a full bash), and reboots to test take a long time.

---

