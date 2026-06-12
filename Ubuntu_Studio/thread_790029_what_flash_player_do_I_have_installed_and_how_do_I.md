---
title: "what flash player do I have installed and how do I remove it"
date: 2008-05-11
forum: Ubuntu Studio
---

### Post by nicol_bolas on 2008-05-11
I get this for all my flash videos

[IMG]http://i298.photobucket.com/albums/mm276/the_dog_man/arrow.jpg[/IMG]

I know if I click on it, the video will play but I want to install adobe.

Please help

---

### Post by virgult on 2008-05-11
sudo apt-get install flashplayer-nonfree
This package downloads the official Adobe plugin from their site and does the job automatically.

---

### Post by nicol_bolas on 2008-05-12
I get this when I run sudo apt-get install flashplayer-nonfree:

E: Couldn't find package flashplayer-nonfree



And I want to remove the flash player I have already.

Thx

Note: I am using Firefox 2, on Hardy

---

### Post by nicol_bolas on 2008-05-15
Bump

---

### Post by Stochastic on 2008-05-15
go to Main Menu -> System -> Administration -> Software Sources then select the multiverse and universe repositories, then do the sudo apt-get install flashplugin-nonfree

---

