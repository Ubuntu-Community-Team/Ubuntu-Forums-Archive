---
title: "Server with cloud systems"
date: 2012-02-27
forum: Server Platforms
---

### Post by barezi6 on 2012-02-27
Hi everyone
I am learning and trying to create a cloud computing server, on my server computer.
I have a server computer in my house using ubuntu server the last version, and now i need to create a server with cloud computing systems, the goal is: run some aplications that i will install on the server, and all the process is processed on the server, the client computer will only see the results of this processing, nothing is processed on the client computer.
it is possible with ubuntu cloud services? if yes, what i should install or do?

Thanks ubuntu community

---

### Post by nsnidanko on 2012-02-27
I am not sure if "cloud" is what you are looking for. From my understanding of the problem you are looking for a simple server - client architecture.

Application that does all "processing" is located on the server and you have some sort of application client on the "client computer".

---

### Post by barezi6 on 2012-02-27
> **nsnidanko said:**
> I am not sure if "cloud" is what you are looking for. From my understanding of the problem you are looking for a simple server - client architecture.

Application that does all "processing" is located on the server and you have some sort of application client on the "client computer".

yeh it is my objective,the servers do all "processing" and the computers that access to the servers will only see the result of this "processing", the normal computers dont do any "processing", all is done by the servers. It is very important, if anyone can tell some technics or some help, will be great for me.

Thanks again

---

### Post by nsnidanko on 2012-02-28
Well I would say you need to design your application in the client + server mode. So thus you will have 2 parts of application: 1 on the server, which does all processing and the second one is on the client computer, which just shows result of transaction. 
Simply put, your "application" has to consist of 2 components. If you would like to run any application might as well look for a model of the terminal server.

---

### Post by barezi6 on 2012-02-29
> **nsnidanko said:**
> Well I would say you need to design your application in the client + server mode. So thus you will have 2 parts of application: 1 on the server, which does all processing and the second one is on the client computer, which just shows result of transaction. 
Simply put, your "application" has to consist of 2 components. If you would like to run any application might as well look for a model of the terminal server.

hmm, i am thinking on other possibility, because the client computer will not need to have the application on the computer, the client computer will access to a server that will have the applications, and other servers will do all the processing of this application, the client computers dont need to have any programm installed or anything else, they can have a easy access to the programs.

---

### Post by SeijiSensei on 2012-02-29
If these are existing applications that use a GUI, you can tunnel X Windows over SSH, run the application on the remote machine, but view the user-interface portion of the application on the client.

For instance, if you run 

```
ssh -X user@server
```

replacing "user" and "server" with actual names, you'll be logged into a shell on the server.  If you then type "firefox &" on the server, you'll see a Firefox browser window pop up on the client machine.  The processing is being done on the server; only the display is shipped to the client.

Another option would be to write a web application so all the interaction takes place in a browser session.  You could use a language like PHP, or write an application that runs via the [cgi-bin]("http://httpd.apache.org/docs/2.2/howto/cgi.html") interface.  PHP web applications are especially useful if you're designing a system where most of the back-end computation concerns database management.  Apache+PHP+PostgreSQL can be used to create very powerful DBMS apps.

---

### Post by barezi6 on 2012-02-29
> **SeijiSensei said:**
> If these are existing applications that use a GUI, you can tunnel X Windows over SSH, run the application on the remote machine, but view the user-interface portion of the application on the client.

For instance, if you run 

```
ssh -X user@server
```

replacing "user" and "server" with actual names, you'll be logged into a shell on the server.  If you then type "firefox &" on the server, you'll see a Firefox browser window pop up on the client machine.  The processing is being done on the server; only the display is shipped to the client.

Another option would be to write a web application so all the interaction takes place in a browser session.  You could use a language like PHP, or write an application that runs via the [cgi-bin]("http://httpd.apache.org/docs/2.2/howto/cgi.html") interface.  PHP web applications are especially useful if you're designing a system where most of the back-end computation concerns database management.  Apache+PHP+PostgreSQL can be used to create very powerful DBMS apps.


Yeh it is really what i want, i am talking about creating a web application to show the results of a application processing inside of a server, it is like, i have 3 servers, one with windows, other with linux and the last with mac os x, and then with my web application the client can choose the server that he want to use, and run some applications inside of this servers, example:

Server with windows:
i have the office and some games like call of duty per exemple

Server with linux:
i have gimp and other programs

Server with mac os x:
i have  iphoto, and other applications

and then by accesing my web application you can choose the server that you want to enter and then use the programs that you want.

And all of processing of this applications, and systems operatives is made on the servers, the client only see the results of this processings.

It is possible?

Thanks

---

### Post by SeijiSensei on 2012-02-29
> **barezi6 said:**
> It is possible?

I seriously doubt you can do this unless you're a really talented systems programmer with lots of experience in coding for each platform.  Even then, I'm dubious.

---

