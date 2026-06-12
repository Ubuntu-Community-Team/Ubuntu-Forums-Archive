---
title: "How do I grab the source code of a package"
date: 2013-05-10
forum: Ubuntu Application Development
---

### Post by tehhh1337 on 2013-05-10
How would I go about grabbing the source code of a package. For example, the top bar. How would I download the source code to that and then edit it?
Thanks

---

### Post by blackbird34 on 2013-05-10
Well, you'd need to find out the package name for whatever runs the top bar. I presume you are talking about the Unity top bar: getting the source for the whole of Unity would be overwhelming, and I'm not sure if all the elements of Unity are all separate packages or not. 

To get the source code of a given package you do ```
apt-get source **package**
``` (without sudo). You need to make sure you have enabled the "Source Code" option in your software sources, which you can find in the Software Center (Edit > Software Sources) 

This question on AskUbuntu will give you a lot of information to think about:  [http://askubuntu.com/questions/28372/how-do-i-get-the-source-code-of-packages-installed-through-apt-get](http://askubuntu.com/questions/28372/how-do-i-get-the-source-code-of-packages-installed-through-apt-get)

Looking around in the Synaptic Package Manager may help you work out what you are looking for. If you haven't already installed it, it's in the Software Centre or else ```
sudo apt-get install synaptic
```. There is a search bar, you could type in "unity" without quotes and see what package descriptions fit what you are looking for.

EDIT: this question might also help you: [http://askubuntu.com/questions/221899/how-to-download-source-code-with-apt-get](http://askubuntu.com/questions/221899/how-to-download-source-code-with-apt-get)

---

