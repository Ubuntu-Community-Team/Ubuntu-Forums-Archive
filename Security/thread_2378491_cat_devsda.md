---
title: "cat /dev/sda"
date: 2017-11-23
forum: Security
---

### Post by shaun-faulkner24 on 2017-11-23
When using "cat /dev/sda I see the word trojan appear a lot as well as many names of known trojans like Nymaim, Bedep and so on. Here is a snippet:

```
b5928a2d2656ba5ef3001dc04350e5a0:399262:Win.Malware.Nymaim-5165:73
15739e1c0caeb02e3a2ab49dca1e630c:523584:Win.Malware.Nymaim-5166:73
d83bdaa831c5784f98dd9535c406abdd:398848:Win.Malware.Nymaim-5167:73
7f052f366d2db24e665df30a6c57e512:621568:Win.Malware.Nymaim-5168:73
92f97eddf93f2c1b60ad81d5ffe8e7b0:455450:Win.Malware.Nymaim-5169:73
af05d12c942d0b32b7c74f9b6260b7d1:858528:Win.Malware.Nymaim-5170:73
be3b18835ffb457d1adec8eb92454699:704656:Win.Malware.Nymaim-5171:73
a6b90fede77dd72bf3a22fb681174836:460659:Win.Malware.Nymaim-5172:73
9c67bc979b6b8a6a73f0b5bc9892af92:882176:Win.Malware.Nymaim-5173:73
9d521721d18d51a2c05001c6053e0fac:632832:Win.Malware.Nymaim-5174:73
ffcd0c4673e6bafe1d832c0c9c155df2:631808:Win.Malware.Nymaim-5175:73
e82598e1b5ec50ad0a2945d3decc8c47:459481:Win.Malware.Nymaim-5176:73
af8aa6dacd8ce8a1cb315ec8e575dc31:413306:Win.Malware.Nymaim-5177:73
ce7d2a159bf7ee9c9259a2a1562fc5d0:823808:Win.Malware.Nymaim-5178:73
0263a52151c4dbad15aa1f973e0fb667:878080:Win.Malware.Nymaim-5179:73
b9a6b570c06711f5353de0df378d938a:463672:Win.Malware.Nymaim-5180:73
761db21243595084594f3c24800793f6:621568:Win.Malware.Nymaim-5181:73
09b0e76ed51c2915ecb1c883f02541a3:628224:Win.Malware.Nymaim-5182:73
a3602215150edc5eb9c8d7e41e84a26c:492360:Win.Malware.Nymaim-5183:73
eabd837f079d154c08d971f11541ce16:126845:Win.Malware.Nymaim-5184:73
b54adf172042cb0b7b68cbffc500cf02:500351:Win.Malware.Nymaim-5185:73
88c1ade5713a32615b9e65a9d7b8d7fc:514936:Win.Malware.Nymaim-5186:73
255d34cd4244d56643f27b799f62e592:358766:Win.Malware.Nymaim-5187:73
17c3dbd3999be0e50b3b9d620e20b027:645632:Win.Malware.Nymaim-5188:73
ec6ad6c943dd497c46ccd9219471ccf9:458368:Win.Malware.Nymaim-5189:73
c4e1239d87fc4db44b0a56d0e6ec66da:496128:Win.Malware.Nymaim-5190:73
5f7c663c15dd0484274d22a899248523:651776:Win.Malware.Nymaim-5191:73
4ff7c4eab0ab82e7205fe123e1f7057b:637952:Win.Malware.Nymaim-5192:73
7f979bf76fdaea505356ba0133db5bdd:916320:Win.Malware.Nymaim-5193:73
```
I'm running Ubuntu 16.04 LTS.

Does this mean I a infected with various Malware/Trojans and if so how do I safely remove them?

Or is a full hard drive wipe the safest way?

Thanks in advance

---

### Post by DuckHook on 2017-11-23
Welcome to the forums, shaun-faulkner24.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Is your system a dual boot with a Windows partition?

If so, then these are likely signatures from an antivirus app that you have installed. It is also possible that you have antivirus installed in your Linux system. I don't recommend AV apps for strictly Linux boxes precisely because of why you've just posted: false positives.

BTW, malware won't announce their presence so crudely or obviously.

When making these sorts of enquiries, it is important to give a full description of your system.

If you are new to the Linux world and are trying to harden your system the Windows way, you are likely going about it the wrong way. There are some very big differences between Linux and Windows that you should know about. The easiest way to learn about them is to follow the link in my sig: *Security Basics*

---

### Post by vasa1 on 2017-11-24
When I ran just *cat /dev/sda*, I got permission denied.

When I ran *sudo cat /dev/sda*, I got what looks like binary (?) output scrolling by until I hit *Ctrl+C*.

So what exactly did you run and where did you come across that advice?

---

### Post by deadflowr on 2017-11-24
> **vasa1 said:**
> When I ran just *cat /dev/sda*, I got permission denied.

When I ran *sudo cat /dev/sda*, I got what looks like binary (?) output scrolling by until I hit *Ctrl+C*.

So what exactly did you run and where did you come across that advice?

cat /dev/sda will show everything that's currently written to the full disk
interspersing between garbled binary output and any text entries like log files.
I would include the output from images music and video among the binary outputs, since that's typically what those would look like.

Unfortunately cat /dev/sda is outputting everything on the disk and cannot be reliable in determining if anything found is actually within the confines of the partition(s) Ubuntu is using.
That said, the chances of any of those found virus strings actually affecting Ubuntu are slim to none. There all written to run on Windows platforms and not Ubuntu.

If it's really bothering the OP then simply install a virus scanner, preferably one with a remove feature.
Here's quick link with a few options you can look into:
[https://help.ubuntu.com/community/Antivirus]("https://help.ubuntu.com/community/Antivirus")

---

