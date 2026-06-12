---
title: "Apache prob"
date: 2011-04-19
forum: Server Platforms
---

### Post by mjollnir79 on 2011-04-19
Ok I am having a problem here, clearly I got auth right which was a question I had on an assignment. I am not asking for help on the homework, cause I got it done correctly, but even before i put auth I got a permission denied cause i was screwing around with everything and messed apache up, lol  I've got a thread deleted once cause I asked for homework help, but so whoever reads this it's not a homework question! I just screwed up apache while doing my homework, but the assignments done, and we're done with apache in class, and my final wil be in class not at home which is where I screwed it up.


jeff@HTC-linux-BPC-G13:/etc/apache2$ wget localhost/question3 --user=jeff --password=218015
--2011-04-19 20:33:21--  [http://localhost/question3](http://localhost/question3)
Resolving localhost... ::1, 127.0.0.1
Connecting to localhost|::1|:80... failed: Connection refused.
Connecting to localhost|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Reusing existing connection to localhost:80.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://localhost/question3/](http://localhost/question3/) [following]
--2011-04-19 20:33:21--  [http://localhost/question3/](http://localhost/question3/)
Reusing existing connection to localhost:80.
HTTP request sent, awaiting response... 200 OK
Length: 64 [text/html]
question3: Permission denied

Cannot write to `question3' (Permission denied).
jeff@HTC-linux-BPC-G13:/etc/apache2$

---

