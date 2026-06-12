---
title: "Using a laptop touchpad to draw a signature"
date: 2015-10-09
forum: Tutorials
---

### Post by not_insane on 2015-10-09
Today I was faced with a bizarre situation. I was sent an email with a  .doc attachment for me to fill in and sign. However, I do not have a  scanner and was far too lazy to print it off or to find some blank paper  and take a picture with my webcam.

So I wrote a little python program to use the touchpad itself to let me draw a signature.

Available here: [https://github.com/moosd/TouchSigner/](https://github.com/moosd/TouchSigner/)

To use, you just need to make sure pygame and tkinter are installed  (sudo apt-get install python-tk python-pygame) and run signer.py

This will capture your mouse. You can then draw out your signature using  your finger or a capacitive stylus if you want. Press enter to save as a  png (w/ a transparent background) and exit.

Press escape to reset to a blank canvas or q to exit without saving.

Screenshots:
[IMG]https://github.com/moosd/TouchSigner/blob/master/screens/screen1.png?raw=true[/IMG]
[IMG]https://github.com/moosd/TouchSigner/blob/master/screens/screen2.png?raw=true[/IMG]

---

