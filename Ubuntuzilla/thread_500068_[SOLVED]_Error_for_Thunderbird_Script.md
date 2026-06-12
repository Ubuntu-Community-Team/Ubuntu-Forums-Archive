---
title: "[SOLVED] Error for Thunderbird Script"
date: 2007-07-13
forum: Ubuntuzilla
---

### Post by meditator1 on 2007-07-13
I have been searching a little while, but didn't see a solution to my issue posted. I did have trouble downloading the ubuntuzilla script but a post here suggested right-clicking on the files and they saved with no problem. Now when I try to run the script to install Thunderbird this is what I get:

carl@carl-desktop:~$ python ~/ubuntuzilla.py -a install -p thunderbird
python: can't open file '/home/carl/ubuntuzilla.py': [Errno 2] No such file or directory


The problem is I see the files, in /home/carl..., and I realize I am doing something wrong. I am a newbie of about a month or so, and I am thrilled about Ubuntu!! Any help or suggestion would be greatly appreciated.

Thank you.
meditator1( Carl)

---

### Post by meditator1 on 2007-07-13
I'm replying to my own post--I hope this isn't inappropriate!? :)  I was looking back over RogerDavis' post and Nanotube's replies and realizing like Roger that I had a question about the correct directory; confirming for myself that the script was saved in the correct location, a "light bulb" went off in my head that the file was named improperly. It was saved as ubuntuzilla 4.1.1.py or something that effect, but the instructions said it should be saved as ubuntuzilla.py. So I renamed the file, pasted the install command from the instructions into the terminal, and the script ran beautifully and the updated Thunderbird installed without a hiccup!! I hope this helps someone else.

Peace.
meditator1

---

### Post by nanotube on 2007-07-13
great! thanks for resolving your own problems :) :guitar:

---

