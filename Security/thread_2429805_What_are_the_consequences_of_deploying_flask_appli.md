---
title: "What are the consequences of deploying flask application via 0.0.0.0"
date: 2019-10-23
forum: Security
---

### Post by jenniferruurs on 2019-10-23
What are the consequences if I deploy a flask application via 0.0.0.0:5000?

Are there security practices that you could advice me during the deployement of a flask application?

[https://en.wikipedia.org/wiki/Flask_(web_framework)](https://en.wikipedia.org/wiki/Flask_(web_framework))

---

### Post by TheFu on 2019-10-23
> **jenniferruurs said:**
> What are the consequences if I deploy a flask application via 0.0.0.0:5000?

Are there security practices that you could advice me during the deployement of a flask application?

[https://en.wikipedia.org/wiki/Flask_(web_framework)](https://en.wikipedia.org/wiki/Flask_(web_framework))

Too many practices to even touch on the basics in a forum like this.  There are probably a thousand things that need to be done in the application and another thousand things that need to be done on the infrastructure to aid with being more secure.

#1 only allow the minimal access required to accomplish any specific task to the individual who is authorized to perform that task.  Start with that.  Don't allow anyone access to a task who doesn't have a requirement to perform that task.  It is a very simple idea, but the implementation goes through every layer from the WAN firewall, reverse proxy, server firewall, webapp, and DB servers.  That is at least 5 layers of security for every :action: URL, when implemented following best practices.

---

