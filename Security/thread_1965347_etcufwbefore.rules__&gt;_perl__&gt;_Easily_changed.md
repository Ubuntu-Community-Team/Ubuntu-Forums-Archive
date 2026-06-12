---
title: "/etc/ufw/before.rules  &gt; perl  &gt; Easily changed"
date: 2012-04-25
forum: Security
---

### Post by oklokl on 2012-04-25
ufw setup
/etc/ufw/before.rules


# don't delete the [COLOR=Red]'COMMIT'[/COLOR] line or these rules won't be processed
[COLOR=Red]COMMIT[/COLOR]


[COLOR=Red]COMMIT[/COLOR] is trying to create a txt above ..
[COLOR=Blue]-A ufw-before-input -p tcp --sport 80 -j DROP[/COLOR]


A computer novice.
 My bad command
sudo perl -pi -e 's/COMMIT/-A ufw-before-input -p tcp --sport 80 -j DROP\nCOMMIT/g' /etc/ufw/before.rules



error.. Message T^T
Incorrect results >>

 # don't delete the [COLOR=Red]'-A ufw-before-input -p tcp --sport 80 -j DROP
COMMIT' [/COLOR]line or these rules won't be processed
-A ufw-before-input -p tcp --sport 80 -j DROP
COMMIT



How do I change?
Please help me ..




I want the results

/etc/ufw/before.rules

# don't delete the [COLOR=Red]'COMMIT'[/COLOR] line or these rules won't be processed
[COLOR=Blue]-A ufw-before-input -p tcp --sport 80 -j DROP[/COLOR]
[COLOR=Red]COMMIT[/COLOR]

---

### Post by oklokl on 2012-04-25
Sorry .. Please Tell me in English. 
Sorry

---

### Post by oklokl on 2012-04-26
## My bad ways.
 A better way?
Please..

:> Contents     '1234' <-  ''''' This is an issue not recognize it so much ...
[COLOR=Red]'COMMIT'
COMMIT[/COLOR]


:> Change
[COLOR=Red]'COMMIT'[/COLOR]
[COLOR=Blue]-A  ufw-before-input -p tcp --sport 80 -j DROP[/COLOR]
 [COLOR=Red]'COMMIT[/COLOR]


sudo perl -pi -e "s/'COMMIT'/##To change the character##/g" /etc/ufw/before.rules
sudo perl -pi -e "s/COMMIT/-A ufw-before-input -p tcp --sport 80 -j DROP\nCOMMIT/g" /etc/ufw/before.rules
sudo perl -pi -e "s/##To change the character##/'COMMIT'/g" /etc/ufw/before.rules


sudo  perl -pi -e "s/'COMMIT'/##To change the character##/g"  /etc/ufw/before.rules && sudo perl -pi -e "s/COMMIT/-A  ufw-before-input -p tcp --sport 80 -j DROP\nCOMMIT/g"  /etc/ufw/before.rules && sudo perl -pi -e "s/##To change the  character##/'COMMIT'/g" /etc/ufw/before.rules



or

sudo sed -i -e "s_[COLOR=Red]'COMMIT'[/COLOR]_##To change the character##_g"  /etc/ufw/before.rules
sudo sed -i -e 's_COMMIT_-A  ufw-before-input -p tcp --sport 80 -j DROP\nCOMMIT_g'  /etc/ufw/before.rules
sudo sed -i -e "s_##To change the  character##_[COLOR=Red]'COMMIT'[/COLOR]_g" /etc/ufw/before.rules


sudo sed -i -e "s_'COMMIT'_##To change the character##_g"  /etc/ufw/before.rules && sudo sed -i -e 's_COMMIT_-A  ufw-before-input -p tcp --sport 80 -j DROP\nCOMMIT_g'  /etc/ufw/before.rules && sudo sed -i -e "s_##To change the  character##_'COMMIT'_g" /etc/ufw/before.rules

---

### Post by nothingspecial on 2012-04-26
*Thread moved to **Security Discussions**.*

---

### Post by darkod on 2012-04-26
Why are you touching it with perl, are you trying to automate it or something?

Why don't you simply edit /etc/ufw/before.rules with an editor?

---

### Post by oklokl on 2012-04-26
Sorry...

I would like to change easily.

---

### Post by darkod on 2012-04-26
If you have a GUI installed, you can try with gedit:
gksu gedit /etc/ufw/before.rules

Or in terminal with the nano editor:
sudo nano /etc/ufw/before.rules

Don't forget to save the changes after you are done, and disable and enable the ufw.

---

### Post by oklokl on 2012-04-26
Answer Thank you.

gedit and nano can understand and use.

I would like to insert a sentence at a time.

---

### Post by oklokl on 2012-04-26
The advice of others

 Thank you so much for all the answers.



sudo perl -pi -e "s/[COLOR=Red]^[/COLOR]COMMIT/-A ufw-before-input -p tcp --sport 80 -j DROP\nCOMMIT/g" /etc/ufw/before.rules

---

