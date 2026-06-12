---
title: "Cat"
date: 2005-06-30
forum: The Cafe
---

### Post by ATS on 2005-06-30
I need to merge two MP3 files into one playable file via the command line. 

I've tried the CAT command which works, and gives me a file equal to the file size of the two MP3's, but only the first file plays. 

The same with an MP3 utility called mp3wrap. 

Do you know of any other Linux utility or program that will do this?

---

### Post by sapo on 2005-06-30
[QUOTE=ATS]I need to merge two MP3 files into one playable file via the command line. 

I've tried the CAT command which works, and gives me a file equal to the file size of the two MP3's, but only the first file plays. 

The same with an MP3 utility called mp3wrap. 

Do you know of any other Linux utility or program that will do this?[/QUOTE]

try:

lame --decode

decode the 2 mp3 in 2 wav.. use cat to join the avi and then reenconde the mp3.. that should work i think  :-P

---

### Post by sonny on 2005-06-30
[QUOTE=sapo]try:

lame --decode

decode the 2 mp3 in 2 wav.. use cat to join the avi and then reenconde the mp3.. that should work i think  :-P[/QUOTE]
Hey Sapo... It sounds like something you might include in you software.

---

### Post by Takis on 2005-06-30
Try mp3wrap. To split, mp3splt.

---

### Post by sapo on 2005-06-30
[QUOTE=sonny]Hey Sapo... It sounds like something you might include in you software.[/QUOTE]

hehe.. but i m not sure if it works.. i was just guessing  :-#

---

### Post by omegasoul on 2005-07-03
I use hjsplit through wine to join my avi files. It should work with mp3.

---

