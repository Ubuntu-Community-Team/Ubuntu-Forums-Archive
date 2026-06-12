---
title: "GRUB Command line on boot"
date: 2022-11-19
forum: Ubuntu/Debian BASED
---

### Post by geek-ash on 2022-11-19
Hey people. I am a newbie with linux. I dual-booted PopOS! 22.04 alongside Win11 on my about laptop 6 months ago. I was not using PopOS that much, hence moved the Win boot option to the top. But now a days I use PopOS sometimes and hence wanted to see the grub menu on each boot. But that grub boot option probably disappeared from my boot options list. Hence I created a new one from the file "\EFI\pop\grubx64.efi". In the past (around an year ago), I had used similar file to create a boot option to boot into the grub menu.
But now, when I boot into this option, it boots into the grub command line. I enter exit, and then it moves on to the second boot option i.e.- the Win boot manager.
I also have a boot option which directly boots into PopOS, which means I am able to boot into both the OS's. But I still need the grub menu on each boot. 
I ran this boot-repair thing and [http://*******.us/XjrWGD](http://*******.us/XjrWGD) here is my boot-info-summary pastebin
I request the experienced people to kindly tell me if I should proceed with boot-repair's recommended repair option or if some other solution.
Thanks!

---

### Post by ajgreeny on 2022-11-19
Your boot repair link was not working so I attempted a repair which did not work.

Can you please run it again and simply add the given link to a reply of your own. Many thanks.

---

### Post by geek-ash on 2022-11-19
Oops, it seems something went wrong with the boot-info-summary link. Hopefully [this]("http://*******.us/XjrWGD") link works now.
Or use: [http://*******.us/XjrWGD](http://*******.us/XjrWGD)
Edit-1: If there are stars in the above link, replace them with "*******". I don't know what is happening with links on this forum :(
Edit-2: Replace the stars with s_p_r_u_n_g_e. Remove the underscores obv.
Thanks

---

### Post by geek-ash on 2022-11-19
The link still doesn't seem to be working. Here's another try:
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOcAAAA9CAYAAABWUX5pAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAhySURBVHhe7Z0/bxRXF8Yf5wOMFMsjUawUg5NiV1rHKLLst0kUK16lCE3YBjuSY iJGyIKSJFQIGgcPgAOEphmSeMUyIuMSBO7QCS2tC6QjZG2sLRWIs0XyHvun9mdf2vPwiq cZ4fGrGeuXPnLnOfOc85dywGAPwtGyHEMQbGx8cpTkIc5B37NyHEMShOQhyF4iTEUShOQhxlYPj0 ywIEeIgjJyEOArFSYij5BAnXS8hx0EOcaqXiAgh/zS0tYQ4CsVJiKNQnIQ4CsVJiKNQnIQ4CsVJiKPw9T0H8Ke xuxogN82Pfxv1EOwuYy7awf2aMgQpi7OYNRrYnXxZ7TsOepzw7ZI4X Ki7NlIEd/yT5K1cuoFNLHzFg9 1OH6Ji7tZFW2HzwE9Za9kdyKIycx84QysNKkL9iY 0nrDYBb/RjlOzREH/qCxGSmtyHiDFJawt7gfQ3XIZvd3XwMaj14 FU6uAQTqljze3OtZTQFy5jdvg1HizewWJ0k0F7g8lOlLCT7QKMzl7GwsVPM8ZDklCcx41fxrCIbm/LRJ3Gsy2JLwVUqkX9s6GIT1Qkam60o05LhLx4WNTUHGBLq/PdtBhKRbmKwsNweUh/aqPHJHHuzzDEFVG1EXjx7lOkAl/jZyzWtu0Ph6DaLdbR9MqYjX0/kgXFecyUPinDi4gOradY2RRBFSYwZRVVqk6LkCQS5RFAgta 9CVnlxKhuFQSaQZNNJV2k1HPf1ck23lg6OsHW1hJWeM3YRvP9PcrptwBiZNTnDfxZPclXkW2J7fsofn7 GP3OR7OA7frXdpoTB9qX7td/SZw67F8NufH0P1G  icP7/8PHKdjHOF9FjM X8sz9kWFnuddtvf7yOjO0PusQq6baTf3ce4bQ91kAkqGmk24qJrrf2CzcDD6Dmxf2InJ1Wb1XTut7DwZWeCa9v5tQha5ZJiHcWCXpySiCh9i1NGQSJlB2Nbg71f8UxF1oRQjHBfY0s/MOwY1zMi5hvS2nqt3UHygUHi5BCnmtTn4a/fwOkzH5ittmOPdSh98xJnX9jjsn2/HmCkmpiwgl953mk3fdXuzY/qcwF32tep7XiYvB6d HN4 PtLVP0NfG/bnD7zCKiex4ht0UYJ6PoEWrWw3Q2sYwLfHSbQPKh qz7Wfwj7VeO0xyL4UxM6Ij1LedMDrK2r5FPsn9hJL7NNNsPnvgBWTI5nCjSSNyp1eqc61jZipdNCsflmsG/EqO1vgLbD7QetfelRDSlhp0mMo8U5X5CbGqBRv2d3CN9 js  tZ81cjcbN2L7lmY 0hNypBKf6F6rnji3R3Ye4cOZzliuLG/I6EZwNnwI3LqASW8HtbGvsGR3AVfx2Q qXRQRcUXkKv11xnMPF36Udt4EZhMPlV6YL4gMgm2sdgaAK9Of44r9bLCFoL2t7Igk ZkqDklH2FzJG7XkPuz9kqqGNpQ6vfdQtur0y 9p27qv2iWFYvPNZDRPUfpSR f2xiJP3zlanEtNmRjJ6JQkIV5LoyW33RuKWaag1XveFGXnRSLa6vHJnCoYu3r7rAguOEgXSmy7NvPTKEn0WF8 vL83YakpPYjAv1O2vRuJQlAKmfyVQoAgtLd291EE xn9tf6SO QhTC19VaZtV2JNZG1XdHW 2RRB64Pd0cUdE6EfqByS9J0ctlaijrJ7wQiqNn9KWtVeaDXTIu4fc1BBSy4SiZpdKA7JJFQPnWheqLYM 9sr4ixOq0g9ct72mX6wpQpBMYqoVlSit4G7K1sSycs4p/LHI liP 2Sisk703muiaymomvyzb86D7KEsPuCf0p6POTBRDQ5C0Ji98ZM7hTmkqnCSjeyoliU7QO5TceAvq5EzkheGN2i1rlNL2Nd gof6r7CB1u0kJRdCAqJVWdbT6HTz4y1z/zYJRVV MnKIbUAVd5pxhWz2jFh9wdtq9sFJ9KNnOLsEOaSnh 9WR5K00mxzqFSEvuUJ4rJ bHuhPnpouztlXtYbchMGhlLW/BbY/GIaO16etxH0etY1YPtEXYi53UvBAnazopwI9XZRq0uUk2uffaGWVKR76vuSVIY4csKIsB0RLPFqcI0qv2orsr3U28P9bP6e1LJURC6jyexKHkTOq1L5I7e5OXYEsPt jVMZuV0SZbq0HqqRqyfXHNhsndpKpZm6iIEiVSxiutNPKkmzepVPBAX4E1eS9j0OTysh ea5Re95KPIOdb55cfx5Rb9YAhg/skOKwRZO5sSbrg2 BYC0UsqHgqFrGubyOoVClqculAURfJLlVcWKnZ5JoHOYXOgXglckO/XXL2D2lE5LckXOX2ZwNGcTC2rxG2fsod1 JH8rTqyg9qZj3DhyLAZRpZOTvvqG2AxVV3Ni8qRpT9VkAn72x3DC7XPtghRLkAtCymbHo771e41 C ild4oecfqx3NZvaxi/y26FoLU qSys9nVWbP2KfqsRNY2e8IuqQhZRSMTWYXoK3sRzBtJdQSjM/EqrWyqcJUes0T6ZDvUdQGJwszH27/4rhbgrxfRCCefs5j1WtQ eLulnLdEv1CuJukbvO0TRb9crt5zzXqdjpwIes45/7XErOUxEb7tc9QaYg60lQxfFCAnkpMnThXJk uLap/knMH6neON7q2nuNsPW9dHkRN3OYG21tjXZPln55jtbD8wv2NpPrOocvLhL1sT4ij/nZyTkH8ZFCchjkJxEuIoOXLOv XPgPkfU5idEvKPwYIQIY5CW0uIowyMj48zchLiIIychDgKxUmIo1CchDgKxUmIowxcunSJBSFCHGRgcHCQ4iTEQWhrCXEUipMQR6E4CXEUipMQR6E4CXEUipMQR6E4CXEUipMQR6E4CXEUipMQR6E4CXEUipMQR6E4CXES4P qQQQHrrICIwAAAABJRU5ErkJggg==[/IMG]

---

### Post by ajgreeny on 2022-11-19
I have also tried again but still no luck; can't even get the word *********** to stay in the text!

Try running boot info script again to get a new link.

---

### Post by geek-ash on 2022-11-19
The link is: s p r u n g e .us/XjrWGD
Just remove the spaces in the above given link and you should be able to see the boot-info-summary-pastebin.

Edit-1: Or try [this]("https://tinyurl.com/y68bwxkf") [https://tinyurl.com/y68bwxkf](https://tinyurl.com/y68bwxkf)

---

### Post by oldfred on 2022-11-19
Boot-Repair normally gives link to pastebin site.

You should only have one ESP per drive.
Many systems will not work with more than one, although UEFI does allow it, and it seems your system is working ok with it?

When grub sees more than one install, it should automatically show menu.

Not familiar with your 31_linux_zfs.
Is that something grub adds for zfs systems or something unique to PopOS!?

With 18.04 or later to always see menu
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT_STYLE=menu

---

### Post by Paddy Landau on 2022-11-23
By default, Pop!_OS uses Systemd-boot, not Grub, unless installed in legacy mode. As I understand it, Windows 11 doesn't allow legacy mode, so you'll have Systemd.

You can check with this command:
```
[ -d /sys/firmware/efi ] && echo 'Installed in UEFI mode' || echo 'Installed in Legacy mode'
```
If it's installed in UEFI mode, you have Systemd, not Grub.

I don't know Systemd, sorry. As System76 creates Pop!_OS for its hardware, read [System76's help]("https://support.system76.com/articles/bootloader/"). If that doesn't help, maybe someone here knows Systemd, or you can ask on Pop!_OS's support forums?

Side note: I wonder why Ubuntu Forums doesn't like "s&#1088;runge"? I can find very little about it in an internet search, none of which is offensive. (I used unicode to display the word, which is why you can see it.)

---

### Post by geek-ash on 2022-12-04
I just removed the older one and installed the grub again. It works now.
Thanks!

---

### Post by geek-ash on 2022-12-04
> **Paddy Landau said:**
> By default, Pop!_OS uses Systemd-boot, not Grub, unless installed in legacy mode. As I understand it, Windows 11 doesn't allow legacy mode, so you'll have Systemd.

You can check with this command:
```
[ -d /sys/firmware/efi ] && echo 'Installed in UEFI mode' || echo 'Installed in Legacy mode'
```
If it's installed in UEFI mode, you have Systemd, not Grub.

I don't know Systemd, sorry. As System76 creates Pop!_OS for its hardware, read [System76's help]("https://support.system76.com/articles/bootloader/"). If that doesn't help, maybe someone here knows Systemd, or you can ask on Pop!_OS's support forums?

Side note: I wonder why Ubuntu Forums doesn't like "s&#1088;runge"? I can find very little about it in an internet search, none of which is offensive. (I used unicode to display the word, which is why you can see it.)

Yup I found this at other places also that Pop!_OS uses systemd. But reinstalling the grub does the job for me. Now I can see the Grub menu on each bootup.
Thanks!

---

