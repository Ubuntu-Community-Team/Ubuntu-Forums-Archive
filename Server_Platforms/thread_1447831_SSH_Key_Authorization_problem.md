---
title: "SSH Key Authorization problem"
date: 2010-04-05
forum: Server Platforms
---

### Post by cK` on 2010-04-05
Hello, i am very new to unbuntu or linux in general.
I just got unbuntu server edition installed on my server along with openssh-server.

Now i am trying to set ssh so i can log in with a key authentication. I am using this guide to do it through putty on my windows machine.   [http://support.suso.com/supki/SSH_Tutorial_for_Windows](http://support.suso.com/supki/SSH_Tutorial_for_Windows)
 

After i installed ssh i logged in correctly. I then procceed to generate a key in putty. 
Now my problem starts when i try and put that key onto my server.
The tutorial says to type in 


mkdir .ssh

My server says it  cannot make that directive because it is already created. 
So i proceed to the next line. I believe this code sets permissions?

chmod 700 ~/.shh
nothing happens just goes to a new line

then i did this 

cd .ssh

nano -w authorization_key

then i copyed and pasted the key i got from putty gen into this file pressed cntrl o and then cntrl x

when i try logging into my server using the key auth it simply asks for my login, once it is input it says authorization invalid then ask for my password.

Any feed back is much appreciated.


-Thanks!

---

### Post by gordintoronto on 2010-04-06
How was this solved?

---

