---
title: "tomcat6 servlet logging question"
date: 2011-01-02
forum: Server Platforms
---

### Post by midnight1111 on 2011-01-02
I am writing my first java servlet and want to get logging working.   The code looks something like
public class SubscriberServlet extends HttpServlet {

   
    private static Logger logger = Logger.getLogger("SubscriberServlet.logger");
    static final long serialVersionUID = 1;
  
    public void init(ServletConfig config) throws ServletException {
        super.init(config);
        logger.info("Starting SubscriberServlet.init");
 }

I have edited the /usr/share/tomcat6/conf/logging.parameters file to include ALL logging messages, but nothing shows up in the log files...
I would appreciate some pointers...
M-

---

### Post by midnight1111 on 2011-01-03
Got it figured out.  The messages are going to catalina.out not the dated log files.
M_

---

