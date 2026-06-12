---
title: "x-server on ubuntu-server"
date: 2007-04-20
forum: Server Platforms
---

### Post by jpgeerets on 2007-04-20
hi folks,

i have an ubuntu-server running with no gui, just only clui.

sometime i want to connect the server with x. running for example cygwin on my windows machine and connect to a graphical desktop on the server.
is that a possibility?

i also want to read for example pdf files on the server. when connecto with ssh to the server, i guess it isnt possible. should i use ssh -X <fqdn> and read the pdf in graphical way?

anyone any idea?

the normal situation of the server is without X. there is also no monitor connect to... :-)

thanks in advance!!

Jean-Paul

---

### Post by b3nw on 2007-04-20
I believe you'll still need to install the xorg packages to do this. Then you could tunnel the x session through SSH .

---

### Post by az on 2007-04-20
1.  You can run an Xserver without the X client (or is it the other way around?) remotely.  You just are not running any session on the local machine.  
2.  Exactly what do you want to do with the pdf?  The PDF should be read on a pdf reader on the client machine if you serve it through a web server or a file server.  If you want to display a pdf file through an X client, you will need to have that software running on the server, but just displaying the contents on the remote client's screen.

---

### Post by jpgeerets on 2007-04-20
hi az,

2.
at this moment i can connect using ssh -Y <fqdn>
so i can install a pdf reader on the server and read the text. all files r on server and i can read text on my monitor.

i dont want every time if i read a pdf (for example), download this file to my local machine.
so this seems to be a good solution i tink.

1.
i think there should be an x-something on my server.
so my (windows)pc can connect to the server and display it's contents to my pc.
or...
should i only have to run an x-client on my server and use x-server on my client.....
at this moment im trying to install xorg on my server...
in worst case i have to re-install ubuntu-server.... 
i hope this isnt nessesary....


Jean-Paul

---

