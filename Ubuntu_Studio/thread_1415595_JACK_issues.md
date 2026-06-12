---
title: "JACK issues"
date: 2010-02-25
forum: Ubuntu Studio
---

### Post by Patricrawley on 2010-02-25
Everything works until I open and close rosegarden. After that my jack server won't run anymore. How do I fix this?

---

### Post by trulan on 2010-02-25
How are you starting the Jack server?  Are you starting it with Jack Control?  By command line?  If you start Rosegarden without starting Jack, it will attempt to start the Jack server.  So it is better to start jack first, at least until you know everything is working.

Is Jack giving you any error messages?

---

### Post by Patricrawley on 2010-02-25
I figured it out, I was previously running jack without a realtime server. Then I installed one and I forgot to uncheck the realtime box in qjackctl.

---

