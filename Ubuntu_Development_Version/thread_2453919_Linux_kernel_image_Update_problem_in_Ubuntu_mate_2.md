---
title: "Linux kernel image Update problem in Ubuntu mate 21.04 daily build.How to update?"
date: 2020-11-19
forum: Ubuntu Development Version
---

### Post by parkjinhyun182 on 2020-11-19
[FONT=Arial]I am using ubuntu mate **21.04 (Hirsute Hippo) daily build**.I am running it inside **virtual box 6.1**[/FONT]
[FONT=Arial]I have allocated **2 cores and 2gb ram** to the virtual box.[/FONT]
[FONT=Arial]I updated the system using** "sudo apt update && sudo apt upgrade -y && sudo apt dist-upgrade -y && sudo apt autoremove -y"**[/FONT]
[FONT=Arial]I saw Linux image update from 5.8.0.26-generic to different versions[/FONT]
[FONT=Arial]There are 3 versions[/FONT]
```
linux-image-generic/hirsute-proposed 5.8.0.36.32+21.04.34 amd64 [upgradable from: 5.8.0.26.31]

linux-image-generic/now 5.8.0.26.31 amd64 [installed,upgradable to: 5.8.0.30.32+21.04.34]

linux-image-generic/hirsute 5.8.0.25.30 amd64


```[B][FONT=Arial]I want to update to the hirsute-proposed version* (linux-image-generic/hirsute-proposed 5.8.0.36.32+21.04.34 amd64 [upgradable from: 5.8.0.26.31])*[/FONT]
[/B][FONT=Arial]**Even after rebooting several times I can't seemed to update to the hirsute-proposed version. How can I update to that version?**

[/FONT]
[FONT=Arial]I am adding the images[/FONT]
[ATTACH=CONFIG]287385[/ATTACH]


[ATTACH=CONFIG]287386[/ATTACH]

---

### Post by slickymaster on 2020-11-19
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by P-I H on 2020-11-19
I think you need Virtualbox 6.1.14 to support kernel 5.8.
[https://9to5linux.com/virtualbox-6-1-14-released-with-full-support-for-linux-kernel-5-8](https://9to5linux.com/virtualbox-6-1-14-released-with-full-support-for-linux-kernel-5-8)

---

### Post by parkjinhyun182 on 2020-11-19
I am already using virtual box 6.1.14

---

### Post by parkjinhyun182 on 2020-11-19
ok.I will remember it

---

