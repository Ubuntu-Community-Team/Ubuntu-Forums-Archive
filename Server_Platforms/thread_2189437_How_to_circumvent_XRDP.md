---
title: "How to circumvent XRDP ?"
date: 2013-11-22
forum: Server Platforms
---

### Post by hadrien15 on 2013-11-22
Hello,
I have an Unbuntu (v12) computer accessed by windows computers through XRDP.
I cannot access to ubuntu anymore probably after wrong manipulations described below. 

When I want to connect the XRDP connection log says:

[FONT=courier new]connecting to sesman ip... port...
sesman connect ok
sending login info to sesman
xrdp_mm_process_login_response: login succesful for display...
started connecting
connecting to ...
error - probelem connecting[/FONT]

I am completely stuck at this point as I have no acess to the terminal.

I am an Ubuntu padawan, so I will tell you exactly the last actions done before the problem arose. I created a folder at the root of ubuntu (/folder). I added scripts files within the folder and ./bash_all file containing the line export PATH=/softcommun/nomlogiciel :$PATH.
sudo chmod &#8211;R 755  within /folder.
In the Home, I modified the .bashrc by adding under the comments « Alias definitions » 
if [ -f /folder/.bash_all ] ; then
. /folder/.bash_all
fi

The idea was to make available some executables to all the users, and it worked.
While I was doing the same for a second software I accidentally done sudo chmod &#8211;R 755 in my Home instead of /folder. I immediately killed this ongoing action and this probably the origin of the problem. 
When restarted the terminal, it was impossible to write a command line and the following sentence was printed: « getpt failed : no such folder or files».
I restarted the computer, but I now cannot access to ubuntu because of the XRDP connecting problem.

I thank you in advance,

---

