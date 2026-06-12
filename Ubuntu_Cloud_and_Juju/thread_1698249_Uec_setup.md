---
title: "Uec setup"
date: 2011-03-02
forum: Ubuntu Cloud and Juju
---

### Post by thedarksinz on 2011-03-02
Hello guys,
we are setting up a new private cloud environment using UEC...
we are checking the links given in the ubuntu forms and other sites in google but they have not giving proper step by step information so can any1 please help me......
i am new to UEC...

---

### Post by raymdt on 2011-03-02
[https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC)

[http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf](http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf)

---

### Post by thedarksinz on 2011-03-02
> **raymdt said:**
> [https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC)

[http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf](http://cssoss.files.wordpress.com/2010/12/eucabookv2-0.pdf)

but according to the pdf we need to have 2 servers..... but we just need 1 server right ? can u give me any link of video or method on how to initialize the connection between the node and the server ( have already installed node and server  on diff computers )

---

### Post by raymdt on 2011-03-03
You can use this tutorial. It's very good explained.

[https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)

---

### Post by thedarksinz on 2011-03-07
actually wat we are doing right now is ....


  we have setup server is one computer and in another computer we have setup a node...
we tried it in our home using 3 laptops ( 1 server 1 node 1 user ) ... we used our router for this.... over there it worked fine, but when we bought our laptops to college and tried here... the page (i.e ip + 8443 ) its not opening .....we tried with lan and with wifi  but the page doesn't open.....

 so my question is it necesary to have a internet line for the setup ?

---

### Post by thedarksinz on 2011-03-07
ok now i am actually done with installing the server and the node.... and connectd them..... now am able to log in with a diff comp ( client ) and create a acc and stuff .... log in and allow access with admin n stuff.........i just downloaded some machine images ... can u guys tell me wat 2 do next ? 
i downloaded the credentials zip file and did all the stuff like changing permission n all those things . nw i saw in a video i just choose " how to run " link and   write the secret key  it says   failed to find key pair   pls help me ........
after this :

can any1 give me examples of wat i can do  now ?  any stuff  which ppl usually do now   cause i have no idea wat i have to do ...... THANK YOU

---

### Post by raymdt on 2011-03-07
Hi,
i suggested you to use this tutorial
[https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)

So you have to make "step-7" from the tutorial ( add key pair )

---

### Post by thedarksinz on 2011-03-09
yea ty man   now even when i follow those steps same error comes .... it says fail to 113 no root 2 host when i do this step  


2.) You must also allow access to port 22 in your instances: euca-authorize default -P tcp -p 22 -s 0.0.0.0/0



using elastic fox it says   xml doc null   

wats wrong pls ?

---

