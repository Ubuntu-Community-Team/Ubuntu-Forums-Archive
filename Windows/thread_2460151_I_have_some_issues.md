---
title: "I have some issues"
date: 2021-04-03
forum: Windows
---

### Post by qazwsxedcrfv64 on 2021-04-03
I use a laptop that once had enough space to be able to dual boot with windows and ubuntu but, now since I am using primarily windows, I can't afford to have ubuntu take up that space. I really like the operating system and think its great, but I want to know how to safely remove it without bricking my laptop or messing it up.
Another reason I want to uninstall it is because if I accidently load into ubuntu while windows wasn't fully shut down, my computer panics and messes up the Wifi, Time, Bluetooth, and other things.
Please help me.

---

### Post by TheFu on 2021-04-03
[LIST=1]
[*]Run Microsoft's partitioning tool and remove/delete all the Linux partitions. If you don't know which to remove, post that data and we can guess.
[*]Use the Windows rescue disk to "fix" the boot process - at least in the way that MSFT thinks "fix" means - only boot Windows.
[/LIST]
Or
[LIST]
[*]Reinstall Windows - it will take the entire drive and wipe everything for you. Is that what you want?
[/LIST]

Clearly, backup anything you don't want to lose before doing either of these. That includes Windows files. It is very common for people not used to dealing with partitions to make mistakes and delete stuff they shouldn't.  Would be best if your backups also had been fully tested via a restore. Backups without a restore test really aren't backups, they are just "wishful thinking."

---

### Post by qazwsxedcrfv64 on 2021-04-03
I want to keep all my windows files and what is a Windows rescue disk?

---

### Post by grahammechanical on 2021-04-03
> what is a Windows rescue disk?

[https://support.microsoft.com/en-us/windows/create-a-recovery-drive-abb4691b-5324-6d4a-8766-73fab304c246](https://support.microsoft.com/en-us/windows/create-a-recovery-drive-abb4691b-5324-6d4a-8766-73fab304c246)

Regards

---

### Post by TheFu on 2021-04-03
> **qazwsxedcrfv64 said:**
> I want to keep all my windows files and what is a Windows rescue disk?

These are all Windows questions. Perhaps asking in a Windows-centric forum would get better results?
[https://support.microsoft.com/en-us/windows/create-a-system-repair-disc-3b4640fd-d3da-3dce-8288-3121161c416e](https://support.microsoft.com/en-us/windows/create-a-system-repair-disc-3b4640fd-d3da-3dce-8288-3121161c416e) seems to be for win7.  I haven't seen any newer versions of Windows, sorry.

Google found this for Win10: 
[https://www.pcworld.com/article/3140449/everything-you-need-to-know-about-windows-10-recovery-drives.html](https://www.pcworld.com/article/3140449/everything-you-need-to-know-about-windows-10-recovery-drives.html)

---

### Post by qazwsxedcrfv64 on 2021-04-03
> **TheFu said:**
> These are all Windows questions. Perhaps asking in a Windows-centric forum would get better results?
[https://support.microsoft.com/en-us/windows/create-a-system-repair-disc-3b4640fd-d3da-3dce-8288-3121161c416e](https://support.microsoft.com/en-us/windows/create-a-system-repair-disc-3b4640fd-d3da-3dce-8288-3121161c416e) seems to be for win7.  I haven't seen any newer versions of Windows, sorry.

Google found this for Win10: 
[https://www.pcworld.com/article/3140449/everything-you-need-to-know-about-windows-10-recovery-drives.html](https://www.pcworld.com/article/3140449/everything-you-need-to-know-about-windows-10-recovery-drives.html)


Is there a chance for my system to become completely unusable because the recovery fails?
Does the USB drive have to be formatted in a certain way?

---

### Post by tea for one on 2021-04-03
Do you have back-ups of your Windows data?

If not, boot into Windows and back up now.

With back-ups, it does not matter if any recovery fails because you can always re-install and restore back-ups.

---

### Post by qazwsxedcrfv64 on 2021-04-03
> **tea for one said:**
> Do you have back-ups of your Windows data?

If not, boot into Windows and back up now.

With back-ups, it does not matter if any recovery fails because you can always re-install and restore back-ups.


How do I know if I have back-ups
Do you mean like a entire copy of all my files on a separate drive? If so, no I don't and I don't have anywhere I can put a backup of all my files.

---

### Post by TheFu on 2021-04-03
> **qazwsxedcrfv64 said:**
> How do I know if I have back-ups
Do you mean like a entire copy of all my files on a separate drive? If so, no I don't and I don't have anywhere I can put a backup of all my files.

You would have gone out of your way to make backups.  If you haven't, don't change anything until you do.  Your data is at risk enough already. Not having backups is like having diarrhea but not wearing underwear. It is just a matter of time before a blowout, or much worse, happens. :oops:

A 2-4TB HDD is $$30-$50.  Create some backups, please.

---

### Post by tea for one on 2021-04-03
> **TheFu said:**
>  Not having backups is like having diarrhea but not wearing underwear. It is just a matter of time before a blowout, or much worse, happens.

That is a metaphor, which would be difficult to improve ;)

---

### Post by qazwsxedcrfv64 on 2021-04-03
> **TheFu said:**
> You would have gone out of your way to make backups.  If you haven't, don't change anything until you do.  Your data is at risk enough already. Not having backups is like having diarrhea but not wearing underwear. It is just a matter of time before a blowout, or much worse, happens. :oops:

A 2-4TB HDD is $$30-$50.  Create some backups, please.


I don't have any money to buy extra space right now, because I bought a drive for games and it isn't gonna be here for a while.
So I shouldn't attempt the deletion before my drive comes correct?

---

### Post by rbmorse on 2021-04-03
Correct

---

### Post by qazwsxedcrfv64 on 2021-04-03
> **rbmorse said:**
> Correct

So should I try it when my ssd expansion for my laptop comes in about a week?

---

### Post by rbmorse on 2021-04-04
> **qazwsxedcrfv64 said:**
> So should I try it when my ssd expansion for my laptop comes in about a week?

Actually, my previous answer wasn't complete. You should wait to remove Ubuntu until you backup your important user data files.  The backup should not be kept on the same storage device that also holds data you need to backup so using your new SSD probably isn't the best thing to do. Get a separate device to hold the backup.

Also, before you try to remove Ubuntu, you should have the Windows rescue device mentioned earlier, just in case.

---

### Post by qazwsxedcrfv64 on 2021-04-04
> **rbmorse said:**
> Actually, my previous answer wasn't complete. You should wait to remove Ubuntu until you backup your important user data files.  The backup should not be kept on the same storage device that also holds data you need to backup so using your new SSD probably isn't the best thing to do. Get a separate device to hold the backup.

Also, before you try to remove Ubuntu, you should have the Windows rescue device mentioned earlier, just in case.

My new SSD is gonna be a second storage space, my boot drive isn't changing.
With the SSD is coming a cord to plug into my laptops motherboard and I was thinking of doing the backup to that since I don't have another thing to back my stuff up to.

---

### Post by rbmorse on 2021-04-04
I want to say that's better than nothing, and in some ways it is, but in other ways it would be misleading.  

I can't set priorities for you....only you can make the decisions about whether having a good backup of your data is more important than other things you want to do. You have to make that decision and act accordingly.  

If you were me you wouldn't even turn on a laptop until you had a solid and tested backup process in place because I believe with all my heart that laptops were invented with sole purpose of losing data.  But if you don't look at things that way I can respect that, but I'm also really limited in what I can do to help.  

You've had three or four people here tell you that making a good backup of your data is the first step.  Using your new SSD to hold a copy of your important data while you mess with the operating system is not a bad idea, but it's far from proper backup.  But, maybe that's a risk you're willing to take.  And if it is then I wish you success and good luck.  In all likelihood you will be able to do what you want with no problem. And if you have a problem we'll be here to help, if we can.

---

### Post by qazwsxedcrfv64 on 2021-04-04
> **rbmorse said:**
> I want to say that's better than nothing, and in some ways it is, but in other ways it would be misleading.  

I can't set priorities for you....only you can make the decisions about whether having a good backup of your data is more important than other things you want to do. You have to make that decision and act accordingly.  

If you were me you wouldn't even turn on a laptop until you had a solid and tested backup process in place because I believe with all my heart that laptops were invented with sole purpose of losing data.  But if you don't look at things that way I can respect that, but I'm also really limited in what I can do to help.  

You've had three or four people here tell you that making a good backup of your data is the first step.  Using your new SSD to hold a copy of your important data while you mess with the operating system is not a bad idea, but it's far from proper backup.  But, maybe that's a risk you're willing to take.  And if it is then I wish you success and good luck.  In all likelihood you will be able to do what you want with no problem. And if you have a problem we'll be here to help, if we can.


Thanks, I will try that when it arrives later this week and I'll consult this forum when I try it.

---

### Post by qazwsxedcrfv64 on 2021-04-12
Can you tell me which one the ubuntu partition is?
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAsIAAABjCAYAAACRzWa7AAAgAElEQVR4Ae19PY8ly3Fl/wvJkS2HoEGAA7ANOrRo0aJHowEB/TvWG7etFdZ7fvtjPUtr7K5AjrSUtJQ0BLH7D Yf1CKq6mSejIrMylt9P6ruPQ YV5kR RF5IjLz3Oy8dZ8G/bcrBH744Yfh /fv icMFAOKAcWAYkAxoBhQDFw4Bp5Eum5POnfFxGWMEBACQkAICAEhIATuBIG1A0YR4Qt/0uj5oGGxhnJrDkM5PW//AUY kA8UA4oBxYBiQDGw7xhY41UiwiLCiYRrMu97Mss/8o9iQDGgGFAMKAZOiwER4R0Q3bWg1YnwaUG9hqf0wlMxoBhQDCgGFAOKAYsBEeEDEuE7uZZzuGHYZNF/QkAInA8Bm1OaV fDUy19DAHF48fwO0Jt Jg/BJmM8z6tqxE7IMoWXHAMNo2np/8y6N91MQD25g9hf13shfd94o1NSXPqPv17tHmreLz/OISPwansaTLO 7SIsIiwSN/8ocMmC/472gIve 9/gT ij7EpiQgrPvcQv4rH 49D JjJrsk479MiwiLCIsIiwooB/QXmIjGATUlE P4JyB6I7poNisf7j0P4mMnuWYjwf/75/w72789/ X/j89//8y/D//n3Pw// qdvwx//7T Gf/6XPw1f//e/Db//p38d/vEPf2wybzZO6ekiu20SwMIcpk3jNpMV2Av/2 C/tolJfzy/YFPSnDqe7 5xvike7z8O4WNwKnuajPM 3XUiLCJ82W9e2iYBx5jDtGncZrICe F/G/zvceN99DFhU9Kc0pzaw1xQPN5/HMLH4FT2NBnnfXqVCIMEn3Ii/L9 /8/U6fvw8vQ0PLl/nz5/zWXeX0Z9IeMrC18/D5 s/qfPw1eWh myv5f3y5JYD iWvG0SqGcO06Zxm8kK7IX/bfDfw0YpG87re2xKmlPnxVVxug1PxeM23I4Ub/AxOJU9TcZ5n14lwr//45 G//4//zD8w//4/Un/ckczMSUS /Xzp4kYv7xPxp2NCHNfX4fPn4yAvwzvIWHeD0G2TQJ4mcO0adxmsgJ74X8b/I 02MrWvhjBpqQ51YeX4uqyOCkeL4vvHuIXPgansqfJOO/Tq0T4X/7jL8Pvfve74be//e3wm9/8Zvj1r389/OpXvxp  ctfDr/4xS Gn//858PPfvaz4a///q Hn/70p8NPfvKTkTDnjpicgnyCpH4aPn FrPHsPRF2hBqEe  nwrZJAC9zmDaN20xWYC/8b4P/HhZR2XBe32NT0pw6L66K0214Kh634XakeIOPwansaTLO /RZiPDf/Le/Gf5u Lvhr/7rX3US4e9DQVILAltebXiyU2NHhN9f5qsWdMpsAyvatFPgot0G0b7xibFtEnCMOUybxm0mK7AX/rfB/0iLrWztixFsSppTfXgpri6Lk LxsvjuIX7hY3Aqe5qM8z59FiJsJ8J/ /d/e8KJcCat471gIqwTyXUnxUyE57IjQXYEVkT4/oP8khPNJgv u2Q/altx igxgE1JRFgxv4eYVzzefxzCx0x2TcZ5n 4iwnY94pR/f/jjn6jT6GpEJsLjtQUiwiCz9uW69OW5RIQ/Nb80h7rpKgS16we p7xtErDHHKZN4zaTFdgL/9vgv4eNUjac1/fYlDSnzour4nQbnorHbbgdKd7gY3Aqe5qM8z69SoR9hdPzERHGHeH5i2yesOLUF2 KABF  jR8Gr8A506McTLs2lkQY5Tb2dM2CeBqDtOmcZvJCuyF/23wP9JiK1v7YgSbkuZUH16Kq8vipHi8LL57iF/4GJzKnibjvE/fhAjjjm868XUEdjKSCDSIsN0JRjp8GwTV e7I9s7ILzvCNgnkzWHaNG4zWYG98L8N/ntYRGXDeX2PTUlz6ry4Kk634al43IbbkeINPgansqfJOO/T1yPCxXuE3YkuEWGQ5Om9w3M5kN/5y3E46Q1fjYayY3 un52SYdsk4Bg4Uc8fxuC9Ng7mi2v3qf5u42vhLtwVA4oBxcB9xgA4lT3Nx5z36SsQ4f2 rcGDcat8RIR//PHHQf uj4H5wv67VSyoX60X9xYDtglpTimu9xLXisf7j0VPfH3ex6KI8A5OiXmTMIfZP5Hg65Ngwxz/ Ymi/P0vnvLxZXxs6xmvccL5MjgL1z5cFY99OB05nszHbL/Ps87SIsIHIMLmRP27HAb8oSMiwsL ctgL2/vD1pNe83Ekk /vz/d79GkUe5Fsj7bLpr45EvmTya7hyHmfFhE CBE2R0f/mYNb/0m/jk8PEW5hLJ0QEAIlArzRYA2KZGUt5YTAZRCIYi SXaZ3tXoNBLw/W3nWWVpE MBEGBtMLcikXyfBhpGIcC2CJBcC2xDgjQbrUCTb1rpqCYHTEIhiL5Kd1qpK7wkB789WnnWWFhE MBFuBSE2n1oZ6SeSLCJcixDJhcB2BHijwVoTybb3oJpCoB BKPYiWX LKrk3BLw/W3nWWbpBhOd38tJrz9Ivtp1CHsfXmR3jNWYenGvlLaDQl20anpxhI kNvLXy0ueTYo81MIY/7LmGF roKQSEwIRANH8imfASAtdAIIq9SHYNW9THZRDw/mzlWWfpFSJMBHYktPMvwZ1ChFU2kVwPPvIWFkgb6fLkjIkYp6Nwkj6T3B58PNaoA3/Ycw1T1NFTCAiBCYFo/kQy4SUEroFAFHuR7Bq2qI/LIOD92cqzztL9RPi7nRATMRbBTeTVg3pq3sICdYx0eXIGIobn1jBaq/ IehvzqXeE356fBvvBl9cv8MSX4XX y0mSfXsbnk32/DZ8 /I6ln9  4YKXc9vb8 un65q5yk02zz9sI2N93XIw53Gs9RlHLLuaegf91w/gTgMwADt ba vDrbzjN6tfJBBLCe2RPrSiT7YDeqLgS6EIhiL5J1NaZCu0TA 7OVZ52l 4mw/frby3sibMUvwCU5ftZ4IgrTVQpPoKMy9/9eOw885y2qkLdNw5MzyD4SfdiMam08qt5jDXzgD3t6bEDOEikD6X0i0sfkl9PooOOJfogXdtQ6QxGMhzr 8joT4ZZumImskf/ZDIzhidqqWTiVzYR7IrnlB463xYeJJXmutS/59RCI5k8ku55F6umREYhiL5I9MkZHH7v3ZyvPOkuvEOGJ0E6nMbVrEUR0HVmeOiP994kEf/r8NRE/b9Aj5i0AMW4jXZ6ceSJ2asCu1X9kvcca2MIf9lzgg9PSmdxNBO55eLaT4kLGJA4t9z9BIjs4ZH jHSXRbyL6VKelGwIiPAzfhukE/XlYcFhqN5XDYAPCXRSnjE6FCYydJKP5E8l2Yq7MuHMEotiLZHcOw10Pz/uzlWedpVeIMF2F8F96M9Kbvkg3lxvLPA0l0SUirHvGifCyIyw6kTfS5cnZgoidEM5rdaU//WqEJ3wjEXt G97oz/QFOeMTYZDo5 fp6gSuT8w BdHMc4vINOrO8w5EdeoLRBPEE/X4lHZOY96CdPp4on7QRyrS0oVEOF9vqHU3tj0TX/QHHMI6sw0oO8z5sGwyXIlrIoD1zJ5YYyLZNW1SX4 LQBR7kexxETr yL0/W3nWWbqfCM nueN1h4LQ2ikvEebv34evnz NJHlxNaKo99jXIdgRFoLI26Zh//jeKjaSU0N1rZ70S6yBMfxhzyVOIJv2Z/z8p/mJvBkhnfW4IsDEDURy1hWED7qZ0U0Edya0Tsf1kB6JIU5ScU2DCGZJmDHS Ik2QcgT6RwysV3qmHTndtEWt5G1c2q2E2S2aSvjadXnPOou2pbg6ghE8yeSXd0wdfiQCESxF8keEpw7GbT3ZyvPOkv3E GRxM6E106DP30evtoX5lhOX6AzMjydDNOJsK5GJMLLjrA4RN5Il/37KBFekrcy2qX/2HuEJ3L3PLx9mb4UN5KwRDrfxi/PJeLHxK1CaK1sQXyJcFrbXjeA8JqS09b 8 vwatc00hf1ptNiEFIjsMk21B1PiXGqnGMl1 nRtYlwk6jOdqDMYrzZpGXK1V0WkOTaCGA9syfWmkh2bbvU32MiEMVeJHtMdO5j1N6frTzrLL1ChPmOMJ/60hfePr0MLzgRLq5L4E4xE2E7BbZ8bnfTu4mJcPsBHTFvYQi7bdOwfx8hwth4auEtfX7FmscamMEf9gzxArl9tjc7gCSCCE7XHkDqcGI5ks9LEGHcw8X1jNcv89sWXodXu66Bk2kbHPq3OchyDDx4ggyn8VCZUofx5y/Lpbu//NYJqp SM5lNBB34ti8WT9XnspF9qX0lropANH8i2VWNUmcPi0AUe5HsYQG6g4F7f7byrLN0gwjr6oIH61J5i0G0baTLkzMmYpyOYlf6THJ78PFYow78Yc8Y05n0FYQSVybsg15  wHI5xoRBqmcyGBuayR4jhiiLMjflJ  sMfli9NfDA7XOSpE NvbK32xDXbgVLmu83enrTuc7CaCm2zwibkfDAjk3r2mbnxrhMNi6oPw9k0rf3UEovkTya5umDp8SASi2ItkDwnOnQza 7OVZ52lRYR3cLpscQjHGOny5AxEDM tcbtW/xH1NmY fQe28Ic9Y1xAEPObIqwuCGpx2srEbU77t0uAKII44v6tPRM3RN35LyqoM9qcdCCEmaijftk2TrEx4vxMY0h/ucllW7pEhFM9 0CQ6 Ye4tTUNuy3MoQxj5nxBKnHIOOmJb0yAtH8iWRXNkvdPSgCUexFsgeF5y6G7f3ZyrPO0iLCByHCMRnrj9 1 o qt3FvI8L92KtkLwIzeT B1Oo0uBfb65bjjQZrSyS7rlXq7VERiGIvkj0qPvcwbu/PVp51lhYRPggR/kigYiOqtfHIehHhWlRILgS2I8AbDdaXSLa9B9UUAv0IRLEXyfpbVMm9IeD92cqzztIiwndOhLEJ1YJWep0I12JDciGwFQHeaLDGRLKt7aueEDgFgSj2ItkpbarsvhDw/mzlWWdpEeE7J8L7CtXSGmyQpTTnrqG3PnQ1ImOulBA4BwK80WAeR7Jz9KU2hMAaAlHsRbK1dqTfLwLen6086yzdJMLvL/k1Z/nX4ujVaU9PQ/H6M3p9Wi4fv31i/NENvIt4JqO5P35Vm6s/vrc425XeZ xey2ZfMips2wHh9eAjb6GFtG0anpxhI9lvCJ5u2dqYrqX3WGMk8Ic912xBHT2FgBCYEIjmTyQTXkLgGghEsRfJrmGL rgMAt6frTzrLF0nwl8/D5/fQUL5XcDvwzvkxS/FlWVenhpkFqSViLCR4DXyHP14x/tL5X3FhW0Yxz6fFhZwjJEuT87ujYitjeeaeo81pij8Yc81e1BHTyEgBCYEovkTyYSXELgGAlHsRbJr2KI LoOA92crzzpL14lwcYK6/BnlqSEjvzMRNeLpiG3tRNZOg18 c/n34YXqeiOn/HQSXWtz qEOJt9MzPdJgDFOCwukjXR5csZEDGl FVbxGi16d2vx6qr0ei36VbEiHtvf2J9ebYVXYeVXc E1X71f9If9RdeUubbe ttyNaKGf02OIY44hu/vLV8VVuC56ru59eJX4vgHM3r9VYsBk0  5/HB9/Z8fpt Ta UfZsMI/uL9ysDFD3vDgGsZ/bEnI5ki4GPscKv0Mvvop7ibI4pX5FiLK HjTnl63947vgGld8TAlHsRbKFzUE84r3wi3gMY7D8EaMcm9xTbd2dypxr7 Ue7zHt/dnKs87SnUSYCC8TZLsK8fI kzgmy5XyVtcIs9Vh4jy285J/cS4ixasnvI74FrbdBxHGhmI/qfv2BaGcSYpJjKgsJ5uVweZSlkcr0ztg7QcZQHazJr8fFjrXxriJoH2uV6aT/aU45W6htz5PJsI1/GvyNELDjQlqUpjnhi/waYFnj /GFxgPz 6dvV9e4ZNef03lnp/p3cWjia5 KIvKwC7YMeVz7PL4lb4nBHijwbyOZHnMM2l9faW1ysdLT4xxmdqcyr2OqXG YW2bdKfPHdemsrtCIIq9SJaNrsTj N5yrGdlrMV7rJWJyueerrH3cm/3mvb bOVZZ kuIuyvLYz3e21DTyR4JpojWZ3u78Ynt0SWPRGmqxS v9FoLv/9 5BsSPWMCNPdYZxUM3HfadoCE46xTcOTM8jiALYJi0X8y/AanTbaJ1U6YrRPmDFZfh5eXwPdWN82KOonpc0qXhBiK9ek2Cxr5S6l91ijf/jDnu2 GX/UtudSbri/vr0Nz5GPuCovtl2 mxZtcnHR2tI/NX/N8i/exqi8l/n8bILZvzpeZ66yh0cgmj RbDlQiyMQB69dzikr4dczn59aqbV7rrnjbVV TwhEsRfJlja7uKmtx6fKi46mtfNWe29hyoEz3p tPOssvUKEp sI1bu745fj5usIjqgamfVk2MhraovL 9Nbn8dJ8oLc8ikwp eT50SS7 NEOI5RmqjjZDTCOn8gmAnIYmNwk3Zqd5qMb9 ovVGBzQd6E3J6PIYuiHZsZ13aJprDChH9mP7jRNjjhXE6uZ06GVO15xoxJP90 a44QUb//Oz1Vy5X/mUhy3OrXubzKGny6K8U0Ot5jwjwRoP5HcmWY7d4qRHhWOfniM PfdCcKvo829wpWlVmZwhEsRfJlmaXMbeIrTmuTpWX/VgfdshU9pUPU6C3Wpz  N5b2nHsnPdnK886SzeIMJ3eNk5SQXgLkmvlF2TWn9jOZM2uQfiyPj/274juQub1E4n3ZNwDsIe8hR/ssE3DkzNsJFGYFoTFJiWd1EJXm6Rle3mCWb10upiIW9ZPk5FP32sbV9lDlGuNzcpfQ3/y1QgaCDAm0Zgs5fgwMf2pt0aEzU/jHdsE/vK0a7yfRvqxs SjyYrUTooF812Pv7yPa38BsH64LPLcB8UQ/VSyN32yWP /NwSwntkTcziSLcdtcRWvJ Wcoprjuoc60wkv/uKV5kIt8M42d8geJXeHQBR7kWxpeBmPtb30VHnZT15Lr7n3ljYcP f92cqzztJ1IhySUSO478N7IsZEPq083e3N1xuoTKo3n9im8lymTmCn6xB4S4Sd8nI9Tj/CiXC54I9h7E89Vj6tlqGfJyOfWuaJSXpPgsZTFZCmstVWDhtkrcw19NbHNiIc4D8OZCkvFkm38YZjpw80RV0r7H1sshF/EAG0uMVfXIf7cvKxCy/zedhBz9FOJsikU/KuEOCNBvM4ki0HbXHkY3k5p3w9myfTFzUb17vSB0Oqfba5Q20quTsEotiLZEvDy3isrcenyst aO2k/eGSe2/Z/33kvD9bedZZukqE8x3cfMozXmuwKw10usQnrkWddH/YEVSQYb4aYTJuN9UNrjQY4ab 01ULvJIt6fgNEkE7sGMHTwtDOMY2DU/OsJHkcLWNISCeniQhj fcwGLSjnKajLjfWtwVZT2nrfK0UdUOXbLdObUcU9ZZ6lp6jzWsgD/subSlgj9wK77YbljlOZRid V6RFoET/YdRsA 4rTpa/6qlfNya8PLfB52lM RsJwSKGV15Q6CQDR/ItlyOBZHTIRrc21ZE5I0dyCYn7E8iluWcdoaqs0d15myu0Igir1ItjTaxWNtPT5VXnTEMTbH wX33qLrO8p4f7byrLN0lQj7gspfjkxbLAJfI12enC2ImJt0OZb9hJpP34pTDy6Tay6IjfVR3O3kepzGiWRAzLl5Si/GQzpLXlPvsYYp8Ic9F/bU8K/J0ag96RN/gfmXLwNeGlHIu3w3XaEoX03GPuJ0y1 uHOwdibz3ry/r8/Ogv7wNb mDwUQi8GdrhkXp 0Igmj RbDlqiyMiwtU5VYs3 nJmbU65TscPZ9xn8SHP9TPORz8XXIPK7g6BKPYi2dJwF4 19fhUedGRi7EL7r1Ft3eW8f5s5VlnaRHhg50IGymbFu7ylDGRi3FCzjo eZsnl5FbFue54CbjePJBG9Jic D  zeGBanMBoypa utv1OvRtTwr8mLIZp/0mkwYc5 8z5a9d3cA5Vbfojp8RfZQ0ZP4/I 9mV9Hg2YnPqOgw F9bwTBHijwZyOZMvhWrzkdac pzjeOMZy3enKUI69Zuh9eO4sRyLJfhCIYi SLS0u43HUU6wUMXWqPHXGsWxCOzCgOD7T3pu6u9OE92crzzpLiwgfiAhjQzlqHK/Zfwu99XkqET4q/rJbCFwLAd5oMK8j2bXsUT PjUAUe5HssVE69ui9P1t51llaRPggRBibybFDtW792vgupbd2RYTrfpFGCGxBgDcazN1ItqVt1RECpyIQxV4kO7Vdld8PAt6frTzrLC0ifBAivJ9wO78l2ChrLV9SLyJcQ11yIbAdAd5oMH8j2fYeVFMI9CMQxV4k629RJfeGgPdnK886S4sIiwjvLZ6vao I8FXhVmcPggBvNCLCD L0HQ9T8bhj55zJNO/jVp51ll4nwtXXla29RYFemza Gu04rzPzIF06b3GAPmzT8OQMG8mZ4kXNzAhEWAMc MOewh o6CkE hCI5k8k62tNpYTAxxCIYi SfawX1b4lAt6frTzrLN0mwiMJZgK78pPLxekqEeFCvkagH09vwQPHRORMROz80wuY2lN3hM Pr1p8bASwntkTcy2SPTZKGv21EIhiL5Jdyx71c34EvD9bedZZukGEK7/wNp7u8q 71YiriLAHu5a3kIDONg1PzrCR5NDxr1uBpiaHvvVs1W3pWm2WuvFVSOP7Zqy9/Fqj/Eq3pXx6LZzJ XUy1C69sqZ8jy6VcUnG02ONovCHPbn8pK/hUZOj1dazVbela7VZ6tbxL8tfJmdjYd/717Jdolff59MwxtX4yjr0fw6Mp/ckWzyP/9Jr8j4ypl67KmP8SNcfqBvNn0iWu6iNsybPNeupVt2Wrt6i19TnFOLK12i9xzsoezGRjf/M87CYT87wls4VrWXtB1HSa0JrhSryKPYiWa5ei4 aPNesp1p1W7p6i15Tj8faa1N9C3vMGzbrser92cqzztJ1IlwlvEaQcUo8k93P dfeyl96c W Gmlu1XG/MPfUQ7hrRPw4cgs9OMZIlydnTMSmdG3S1OQ9wc11OW11fb6nPVfGFsJEDGrtteQBER4XV5J/exve8q9SOAPirMcapeAPezL k75lZ2MDROPhk9vktBX2 bCBtrCFv8ex3VJF22tjWW5cuFNcVJr sLjsM26up0xcc5SOGLrNZkM8LnvotcuXs/zT8FS86HTZ qUk0fyJZLl/bz80NTn0rSfX5bTV8flWOxVdY05dJ64rdnWJy/Fvs7dso y2pStL9ufmX11LP9DTXzOKvUiWW6zZX5PnmvUU1 W01fD5eitVTSMeh/HAiPbKaiN7VJTYIFa9pd6frTzrLN0mwp8 D18X1xr4pNhI7dPwhJ9EHq9SgLzyibBP99T5Pnx/fxkysT4OsfUgr XNoShjpMuTMxAxPOuTpgwYHyjtPNfltNXy XZLkdaCN3 ar7XXkgeT2Cb3B0mUxxq2wx/2zLhD27Jzn0S4jX9tPBhvz7O3DV/O53v6OrVMTx89ZWr9TifBl GcvXYF5c7yAac25rY8mj RLLcS2D8qa/Jcs57iupy2Gj5fb6WmufycqvV8Drkfv8/39NGq09L1tF0pY2v hokWxV4ky73W7K/Jc816iuty2mr4fL2VmubY8VgbVYTNhJWv4f3ZyrPO0m0iHJ7IBifC40kvnfbyyW8z7eqMp9B8BE6EeUHI74cYm0PhGCNdnpxBlh1fmzROPp9STX qzUTS/sSU/nybFhXUtafXzzr7/fNZN5HagACE5NR/kkdfeURTqiXP9udak62ZYJumZdOky/Wnn3M /Y5wy04iwkfB328uhd3LU07EgMXQFD6TH5YxxUgj7bEr83Fs4s/JU1w v70Nr0/rOKPH ibDfXO67G/1ys0q4Zzafn19HtBWPM4pPoFjxvZ5eFvMvTy6KeXsH4U8F7ye83Oa rC bWOFLXmOLctmXbYJ65k98UEykuUabE WLnxXxGZeE2I80aY9r72moW8by5TO/l/q2L917IehNc6p/efh RnzcsYxXJPZhmwjfg59vR/C07AdgxVt2pP0hW62qfAj2zu38fYaxN48LzccfkSxF8lm65LPgEdVXoxjx/HoY6BiN/ZPzPvRdTb4ojz8xevLjBD3U9QBNpN/zxGr2SdTyvuzlWedpetE Duf/BLpLK5M8EmvI7W4AnEyEcaJMvV5xyTYnGD/wTEgvUzOsJFkx7uFhhedRBDmBQV/RvrySieyaInL1NJWdu4PC5AFO 7sWjrNlmmhpuzckdXHRKD2kt3Qzf0kOSacrw/77ZnJQ q3ZpOTW23DlrFGy/CHPR8Hfxv95IOE5biYgXSu6VAOKEZPayOXG8kW4qoozuXKfieChja4nJlfi3PamAsCH7XT0yYZaxiFY0CZyf6IMIIkjRtuEJ/wR/rLh5Up5hL3gbFAxhuVG1NxAjXZV/ZB9zGLPl3ZOT7QI57R/IlkKJ/GSXMfm/FTihc3hqqvgQOX57T16sbBY3R MFKY5kMy2Opj3UJ76Hf EJFiYuor 59tieyoYZ86n 1Hf679bvtR39vb2U8RQx4DHmOkI0yDNSbtKeyX0Sxrl3FnW vpKPYiWW5h9suh45HWvCKAnW/SPJrWixynQGPCIjXB/qrGWq2Pqa3UR7U  rZn2Rb2DC5hae/PVp51lm4Q4elqwlNxKjxdhcjXFc5MhEfy/PQQ1yHYEezEfiKcF7EcEBQwY7DSRLAJjUgeFxfo0A7VdYHnA7HMWz0sTF G17T4Z6um8ihjcu7Ll4M9Xs71WTen5/FOQ6zYNJfh2tuJcM3OWX4k/Edb2e4S60QExnIVXdWnjLalzTeIPXuW7U132aAnm4q4ovhp4Zy6pvJJBlvgRyrT1SY1FOBC2jjeozk495s2ibERsivMoydfzuS2sQXjW7Tj67byXjd9 IUVePL6hg SkQzlu9aEll8iPIuY9Ha38qZDXMCj740AAAtYSURBVJ6ypiFufVyv9QUfGRqtsqbOJ6XVDwhjGz321 w9pZ a7Y1xBPMlrTFr4y9iOkfPWiqKvUiW2/H2Q0Py3cfj7BuPd81uXw5DDuSlv4JYq/UR jeoj77Hp2HeiNW5rPdnK886S7eJsJ3EuvcIv7zzSe25ibD/spyuRthpJTaSHBs0GbOwXESD4B2LFvLaRunbb ftE5pt3ngWJo0Zq49gN4FvDzVacq6P8uVz/KQ4k33YgmdZcspFHzpQjifK/eNPJ4dFfExopEWvpav6FIjiWfMx/vwGP1NsWr9NIow66MM/a32ynNLBOH2LZZ7wKxVzjto2SdE jXMuPcZxeGptBVxbc51QXvTj63Ge01EfrOe0lZ3GnsyYE9H8iWS5nm8XGpIX44G hSfVXeDGOmurzGPdwJN6m5NWnuOurF W9zrOc3ppR2FXMX6OG9/GdMK7viYziSWLu/vx/XKe025cRftTv2mNcX4oxj8WtXYZd7K7kYxiL5LlJrz90JA8GMdYqpDX/ETtjJXaecQhnrAmP60 41K2V9Qr7MstlOtSW579VYm1Wh8L/1bqU/fLGCiUKeP92cqzztLrRPjOryV4QG6RN0 i34icbSJiY8DRn9gQLnaiAFIxBisWQ544nLaKK3lr5/l1eE2nT gMT14MovZQzvfDcp7ks/zL25DvcE0bcjpNW7EJmNpz29UI4AYb7cn2W/og C/iwP/ZEthPY8IfFsqFk8fOmPh0o1wzNrNNtqiXp2EBzkW3tT5Z7tNrbRYdpJO6hI2p01sjuG0Lk9oczG3mjcvVLWIsly9jz RWL2MGwprsG08WEcNrfbB areYZ0 vbMiYxnpmT8y1SJYrch9ZWo7L9Y1iVTy5TU5bxZX8yvpRnrZH7cG4SMd9c3qlbNc4535X7ff9kr3d/fg2OM9pPy7TUWyO6w vMYhLX2/ 0IP9i0xeS0axF8lyO95 aFg jSPNhVSkNr993cY4fXyu nNtj/V9R ub20MxHr WFP6CT2z/hw tYgUbPy4rujo2tj0ZtUh4f7byrLO0iPAOiL55FI6xTcOTM2wk2fO1wHDyMWDpTwrjLjgF 3j/riCvZV37xDeWGeuUuuUmMv15NF29yIamVN7YTWTtkV2JMPp UN3kPMlYTu2kXX7Sj2Ng2bj5P6WN2Up5rNEy/GHP 8efF R5YUr 6dcVMcObKUAdnzUfm7IWmxYy U/C7S/L0RWg1G tT5Zz2mMwt1kd09yRn29pw3Zt18ZJY8xXRnxdn8cgTU5zId2rhb7E8On1le5q zZb Uk3fdll6o nGHqL5k8kQ/loTZl0zhaP8dh5LW7KukV8Ljbksqz1vVg/srFjarmmubmSyvu2Oc/psVfyi8/3jRPdtu33/aKWPfv7aWHa0k0fohGvjJu3y VtjkQBx YH6Sj2Ilmu6vpNCic/UDyOBwhYk0K7bZA2PvjFf1iBnP1ldeZ48X4J 3D4zbhuj9XkmMShzK 2Z3v/ct6nRYQPRoSXpCwHwi1TFsh HhT22KTAJCwUl8us2rSZCF/O5q0tr471yviv2rN1oFZvXGCjD0YfaXS97kXHtN79TkrEG5k3jjcarFmRzNfbU37V31eeU6dis2r/qQ3evLwRLk/C oyKYi S9bV2m1Kr/tx5PLZQWx1bq/Ks8/5s5VlnaRHhAxFhbCgdMXHdIp0TcPxE2mTLZzS70ybD9PSrEWe08xxNdY71evgbWbocUbVFM13vOQd XW1cdkxdJuyi0IMQ4d3NqROd32n/ia3etPg47zfuH0x8sI9GspsOsNV5pz vt8a3jD1R1zm2tVa9P1t51llaRPggRBiTdy0YrqvHn9C2fUq/jK2n2XRsInzaWC D9zVaxTjxp7nLkexrjObYfdw7EUas7WlNOyVijm7/KWPtL8vEB3tpJOtv8Vol79mf5x2b92crzzpLiwgfhAi3ph0mdq2M9D/UoNl4R7janBRCQAjQdx5sk8H6w5sPZAJLCFwDgSj2Itk1bFEfl0HA 7OVZ52lRYQPToTXNhTp6yTYpqPhc/irEZdZV9SqENiMAG80WIMi2eYOVFEInIBAFHuR7IQmVXRnCHh/tvKss7SI8IGJMDaYWjxKv06CRYRr0SO5ENiOAG80WIci2fYeVFMI9CMQxV4k629RJfeGgPdnK886S4sIH5QIY3OpBaP06yTYsBMRrkWQ5EJgOwK80WAtimTbe1BNIdCPQBR7kay/RZXcGwLen6086ywtInxAIoyNpRaI0veRYMNPRLgWRZILge0I8EaD9SiSbe9BNYVAPwJR7EWy/hZVcm8IeH 28qyztIjwwYgwNpVaEErfT4INQxHhWiRJLgS2I8AbDdakSLa9B9UUAv0IRLEXyfpbVMm9IeD92cqzztIiwgciwthQagEo/Wkk2HAUEa5Fk RCYDsCvNFgXYpk23tQTSHQj0AUe5Gsv0WV3BsC3p tPOssLSJ8ECKMzaQWfNKfToINSxHhWkRJLgS2I8AbDdamSLa9B9UUAv0IRLEXyfpbVMm9IeD92cqzztIiwgchwq2gw0ZTKyN9nSSLCNeiRnIhsB0B3miw/kSy7T2ophDoRyCKvUjW36JK7g0B789WnnWWFhE OBHGJlMLSunrJNgwExGuRY7kQmA7ArzRYA2KZNt7UE0h0I9AFHuRrL9FldwbAt6frTzrLC0ifGAijA2mFpDSr5NgEeFa9EguBLYjwBsN1qFItr0H1RQC/QhEsRfJ ltUyb0h4P3ZyrPO0iLCByXC2FxqwSj9Ogk27ESEaxEkuRDYjgBvNFiLItn2HlRTCPQjEMVeJOtvUSX3hoD3ZyvPOkuLCB QCGNjqQWi9H0k2PATEa5FkeRCYDsCvNFgPYpk23tQTSHQj0AUe5Gsv0WV3BsC3p tPOssLSJ8MCKMTaUWhNL3k2DDUES4FkmSC4HtCPBGgzUpkm3vQTWFQD8CUexFsv4WVXJvCHh/tvKss7SI8IGIMDaUWgBKfxoJNhxFhGvRJLkQ2I4AbzRYlyLZ9h5UUwj0IxDFXiTrb1El94aA92crzzpLiwgfhAhjM6kFn/Snk2DDUkS4FlGSC4HtCPBGg7Upkm3vQTWFQD8CUexFsv4WVXJvCHh/tvKss7SI8EGIcCvosNHUykhfJ8kiwrWokVwIbEeANxqsP5Fsew qKQT6EYhiL5L1t6iSe0PA 7OVZ52lRYQPToSxydSCUvo6CTbMRIRrkSO5ENiOAG80WIMi2fYeVFMI9CMQxV4k629RJfeGgPdnK886S4sIH5gIY4OpBaT06yRYRLgWPZILge0I8EaDdSiSbe9BNYVAPwJR7EWy/hZVcm8IeH 28qyztIjwQYiwbSb6dxkMfvzxxwH/MLl5okCmpxAQAn0I8PyJiHBfKyolBM6DgOLxPDjuuRXv41aedZYWET4AEQZJ0zMT1kthgYnuJ4ry3wdhIAy2xEBEhLe0ozqKv3PEgOLx/uPIfMyx4vOss7SIsIhwOg29FLk8Ursiwve/SPpFUPnL lzE47L4Kn5Pw1fxeBpeR4wvT3x93o9JRFhEWER45WqEnzTK3/9CKh fz8ciHufDUnH5cSwVjx/HcO9x6Imvz3v7RYR3SIRxKqnnbRCwSaN/wkAxoBhQDCgGFAPHjAEmu ZDzvu0iPAOibB3kvL3/wlWPpaPFQOKAcWAYkAxcP4YEBHeAdFdC2w790SZNYehnJ7nnyzCVJgqBhQDigHFgGLgvmJgjVfpRHgHRFlE L4mnRZR VMxoBhQDCgGFAP7iAER4R0Q3bXJYE7SP2GgGFAMKAYUA4oBxYBi4Pwx0OJhTwL8/IB/FNOWw6TbxydM UF UAwoBhQDigHFwPFj4P8DIlPLd1s we8AAAAASUVORK5CYII=[/IMG]

---

### Post by qazwsxedcrfv64 on 2021-04-12
Nevermind, I deleted the 12 gig one, but I have a new question.
Why is there still a ubuntu boot option in the boot menu?

---

### Post by CelticWarrior on 2021-04-12
UEFI systems always retain the .efi files (In the ESP - EFI System Partition) regardless of OS' partitions having been deleted. There's no problem keeping them. You can and should manage the boot order in UEFI settings > Boot. Depending on the particular firmware it may allow removing some entries. Also possible to do from the OS. With Ubuntu we would use efibotmgr. In Windows I don't know but I'm sure you can find information about it in one of the thousands of online resources dedicated to Windows.

Good bye and good luck in your future endeavors.

---

