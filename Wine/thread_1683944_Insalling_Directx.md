---
title: "Insalling Directx"
date: 2011-02-08
forum: Wine
---

### Post by Steve Moss on 2011-02-08
Hope someone can tell me what's gone wrong

I want to install DirectX

I followed the instructions in this link ....to the letter

[http://www.dedoimedo.com/games/wine-directx.html]("http://www.dedoimedo.com/games/wine-directx.html")

When I click on the dxdiag.exe ( or use the terminal command) nothing happens

Can anyone help me?

---

### Post by sydbat on 2011-02-08
> **Steve Moss said:**
> Hope someone can tell me what's gone wrong

I want to install DirectX

I followed the instructions in this link ....to the letter

[http://www.dedoimedo.com/games/wine-directx.html]("http://www.dedoimedo.com/games/wine-directx.html")

When I click on the dxdiag.exe ( or use the terminal command) nothing happens

Can anyone help me?[Go here]("http://wiki.winehq.org/winetricks"), follow instructions.

---

### Post by Elfy on 2011-02-08
moved to wine

---

### Post by Steve Moss on 2011-02-09
Thanks for the reply

Please bear in mind I am VERY new to this

I have downloaded a text file

I have typed sh winetrick and selected the appropriate DX option (DXd9 or something like that)

It appears to do what it is supposed to

When I click Dxdiag still nothing happens

Sorry for being so thick

Hope you can give more help

---

### Post by dino99 on 2011-02-09
which wine release do you use ? why are you thinking you need to install directx ? Have you some errors logged ?

---

### Post by P4man on 2011-02-09
winetricks is the answer.
open a terminal and type

```
wget http://www.kegel.com/wine/winetricks
```

Make the script exectutable:

```
chmod +x winetricks
```

Then run it

```
sh winetricks
```

Select the DirectX version and any other packages you need from the list.

---

### Post by Steve Moss on 2011-02-11
> which wine release do you use ? why are you thinking you need to install directx ? Have you some errors logged ?

Using 1.3.13

I want to install directx so I can play EQ2....their forums tell me this is required

---

