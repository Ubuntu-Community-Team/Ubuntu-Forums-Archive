---
title: "grant user access to open ports in ubuntu-server"
date: 2010-11-19
forum: Server Platforms
---

### Post by Defrector on 2010-11-19
I have a JavaCL program trying to open a port on 41xxx and it is getting permission denied unless I run it as root. I would like to grant a single user this permission for opening this port. This program runs fine on a vanilla ubuntu install but not on server. Where does Ubuntu handle user permissions for opening ports?

I understand this is typically a no-no on a server but this is an unusual circumstance.

---

### Post by Defrector on 2010-11-19
Just figured it out. It wasn't a ubuntu-permissions problem at all but a java-permissions problem.

Creating a `.java.policy` file in the home directory of the user invoking the program and setting adequate permissions in that file using the information given by [http://docs.sun.com/app/docs/doc/819-3664/6n5sbeo24?a=view]("http://docs.sun.com/app/docs/doc/819-3664/6n5sbeo24?a=view") did the trick.

note: It's almost important to ensure rmiregistry is running in the root directory of the application as well if RMI is being used.

SOLVED.

---

