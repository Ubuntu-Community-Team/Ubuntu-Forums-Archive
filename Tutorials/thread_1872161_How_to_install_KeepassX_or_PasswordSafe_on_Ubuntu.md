---
title: "How to install KeepassX or PasswordSafe on Ubuntu:"
date: 2011-10-30
forum: Tutorials
---

### Post by prashant2402 on 2011-10-30
How to install PasswordSafe or KeepassX on Ubuntu:

Just in case you do not know what KeePassX is, here is a short description…

KeePassX is an application for people with extremly high demands on secure personal data management.I am a HUGE fan of passwordSafe on Windows as it's one of the best password managing tools I had used so far. KeepassX is it's Linux flair but I am afraid it's not that straightforward to install on Ubuntu. KeepassX should be first downloaded from the source code and needs to be built manually. Don't worry, these steps should make it a walk in the park.  

I have tried these steps on Ubuntu 11.04 Natty Narwhal. I am not an expert of Ubuntu but after spending aweful lot of time in installing KeepassX I really wanted other users to not go through the pain so offering this easy installation quide. Do post your comments or questions, I will try to reply if I can.

1. Download the source code from [http://www.keepassx.org/downloads/]("http://www.keepassx.org/downloads/").

2. Unzip it to a directory.

3. You need to install qmake and some additional libraries which is the build tool required to build/install Keepassx. Run the command:
```
sudo apt get-install qmake-qt4
```
Once done, run:
```
sudo apt-get install libx11-dev

```Once done, run:
```
sudo apt-get install libxtst-dev

```Now, you should be ready to install KeepassX from the source code. 

4. Go to the folder where you have unzipped KeepassX in the terminal.

5. Run the command:
```
sudo make

```This should have generated Makefile file in the directory.

6. Run the command:
```
sudo make install

```
If installed successfully, you will see keepassX executable added to /usr/bin
/usr/bin/qmake-qt4 -o make keepassx.pro
If there are any errors, don't just ignore but carefully go through each one of them to understand why the build/install failed. Normal errors that I encountered were it couldn't create or remove some folders due to permissions in which case I had manually created those folders myself and then re-ran the commands. But if you use sudo as prefix to make instal command it should work fine.

To run the application, just run the executable from /usr/bin/keepassx

Congratulations if managed to install it successfully!

Regards,

Prash

---

