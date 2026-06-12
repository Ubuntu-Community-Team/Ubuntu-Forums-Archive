---
title: "Installing Ubuntu via Virtualbox on a new Macbook"
date: 2013-07-11
forum: Virtualisation
---

### Post by Amurko on 2013-07-11
I'm wondering if anyone else is running Ubuntu on a Macbook using Virtualbox.  Is it slow?  Are there any compatibility issues?

Note: I'm not a fan of the Unity desktop and will be using Gnome Classic..  I glanced a few threads here and it seems people are having problems with Unity when running Ubuntu from virtualbox.  Also, I'm also willing to consider Linux mint.  Note that dual booting is not an option (this is someone else's computer and while I have permission to install new OS's via Virtualbox, I'm not allowed to modify it to dual boot.)

---

### Post by rocklobster217 on 2013-07-31
I'm running Ubuntu 13.04 in Virtualbox on MBA and have no issues with speed or compatibility. 

Just adjust the RAM and Video to suit. Play about with 3D/2D and install Virtualbox Additional Extras. I had better results running 3D. 

I will upload a benchmark once it finishes - pending it doesn't list any personal data. If there are other areas you would like more detailed tests ran just let me know. 

But the most conclusive test would be to install it for yourself and see how it performs first hand. If your not happy just destroy and move on with your life :)

Have a great day.

EDIT: removed word

---

### Post by rocklobster217 on 2013-07-31
[h=1]Benchmarks[/h][TABLE]
[TR]
[TD="class: stitle, colspan: 2"]CPU Blowfish[/TD]
[/TR]
 [TR]
[TD="class: sstitle, colspan: 3"]CPU Blowfish[/TD]
[/TR]
  [TR]
 [TD="class: field"]**This Machine**[/TD]
[TD="class: value"]2305 MHz[/TD]
[TD="class: value"]7.557[/TD]
[/TR]
  [TR]
 [TD="class: field"]Intel(R) Celeron(R) M processor         1.50GHz[/TD]
[TD="class: value"](null)[/TD]
[TD="class: value"]26.1876862[/TD]
[/TR]
  [TR]
 [TD="class: field"]PowerPC 740/750 (280.00MHz)[/TD]
[TD="class: value"](null)[/TD]
[TD="class: value"]172.816713[/TD]
[/TR]
 [/TABLE]
[TABLE]
[TR]
[TD="class: stitle, colspan: 3"]CPU CryptoHash[/TD]
[/TR]
 [TR]
[TD="class: sstitle, colspan: 3"]CPU CryptoHash[/TD]
[/TR]
  [TR]
 [TD="class: field"]**This Machine**[/TD]
[TD="class: value"]2305 MHz[/TD]
[TD="class: value"]223.766[/TD]
[/TR]
 [/TABLE]
[TABLE]
[TR]
[TD="class: stitle, colspan: 3"]CPU Fibonacci[/TD]
[/TR]
 [TR]
[TD="class: sstitle, colspan: 3"]CPU Fibonacci[/TD]
[/TR]
  [TR]
 [TD="class: field"]**This Machine**[/TD]
[TD="class: value"]2305 MHz[/TD]
[TD="class: value"]2.622[/TD]
[/TR]
  [TR]
 [TD="class: field"]Intel(R) Celeron(R) M processor         1.50GHz[/TD]
[TD="class: value"](null)[/TD]
[TD="class: value"]8.1375674[/TD]
[/TR]
  [TR]
 [TD="class: field"]PowerPC 740/750 (280.00MHz)[/TD]
[TD="class: value"](null)[/TD]
[TD="class: value"]58.07682[/TD]
[/TR]
 [/TABLE]
[TABLE]
[TR]
[TD="class: stitle, colspan: 3"]CPU N-Queens[/TD]
[/TR]
 [TR]
[TD="class: sstitle, colspan: 3"]CPU N-Queens[/TD]
[/TR]
  [TR]
 [TD="class: field"]**This Machine**[/TD]
[TD="class: value"]2305 MHz[/TD]
[TD="class: value"]5.700[/TD]
[/TR]
 [/TABLE]
[TABLE]
[TR]
[TD="class: stitle, colspan: 3"]FPU FFT[/TD]
[/TR]
 [TR]
[TD="class: sstitle, colspan: 3"]FPU FFT[/TD]
[/TR]
  [TR]
 [TD="class: field"]**This Machine**[/TD]
[TD="class: value"]2305 MHz[/TD]
[TD="class: value"]2.144[/TD]
[/TR]
 [/TABLE]
[TABLE]
[TR]
[TD="class: stitle, colspan: 3"]FPU Raytracing[/TD]
[/TR]
 [TR]
[TD="class: sstitle, colspan: 3"]FPU Raytracing[/TD]
[/TR]
  [TR]
 [TD="class: field"]**This Machine**[/TD]
[TD="class: value"]2305 MHz[/TD]
[TD="class: value"]11.673[/TD]
[/TR]
  [TR]
 [TD="class: field"]Intel(R) Celeron(R) M processor         1.50GHz[/TD]
[TD="class: value"](null)[/TD]
[TD="class: value"]40.8816714[/TD]
[/TR]
  [TR]
 [TD="class: field"]PowerPC 740/750 (280.00MHz)[/TD]
[TD="class: value"](null)[/TD]
[TD="class: value"]161.312647[/TD]
[/TR]
[/TABLE]

---

