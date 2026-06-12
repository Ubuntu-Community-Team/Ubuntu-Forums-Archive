---
title: "Minimal autoinstall.yaml to install authorized keys, getting subiquity/Error/load_aut"
date: 2024-06-12
forum: Server Platforms
---

### Post by garymm on 2024-06-12
[COLOR=#0C0D0E][FONT=-apple-system]I have added autoinstall.yaml to the ubuntu 22.04 server installation USB stick. Upon booting it fails with: subiquity/Error/load_autoinstall_data[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I can enter a shell and cat /autoinstall.yaml and see the file is there as expected.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]The two versions I tried:
[https://gist.github.com/garymm/535c621ccc091781c783346b890f2823](https://gist.github.com/garymm/535c621ccc091781c783346b890f2823)

No clue what's wrong. Thanks for any help!
[/FONT][/COLOR]

---

### Post by garymm on 2024-06-12
Ah I found the answer:
Indenting under the top-level `autoinstall:` key is only supported with ubuntu 24.04 and later. Removing that key and shifting the contents up one level is required for ubuntu 22.04 (and earlier).

---

