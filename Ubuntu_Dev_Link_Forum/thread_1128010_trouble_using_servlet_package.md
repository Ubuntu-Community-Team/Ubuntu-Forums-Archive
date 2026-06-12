---
title: "trouble using servlet package"
date: 2009-04-17
forum: Ubuntu Dev Link Forum
---

### Post by ggankhuy on 2009-04-17
Below is what i have in my HelloServlet.java file

import java.io.*;
import javax.servlet.*;

public class HelloServlet extends GenericServlet
{
	
}


and I tried to build and following errors:

./HelloServlet.java:2: package javax.servlet does not exist
import javax.servlet.*;
^
./HelloServlet.java:4: cannot find symbol
symbol: class GenericServlet
public class HelloServlet extends GenericServlet
                                  ^
I tried to install every relevant package but still no avail. If you could let me know, what package will get rid of this this message, that will be a huge help. Thanks!

---

