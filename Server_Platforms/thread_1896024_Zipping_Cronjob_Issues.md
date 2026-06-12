---
title: "Zipping Cronjob Issues"
date: 2011-12-16
forum: Server Platforms
---

### Post by NateN34 on 2011-12-16
Issue has been resolved after some research.

~Snipped~

I have this init script that will backup the server files every hour. This is done by having the cronjob run the execute the backup function in the script. When I manually run the script, by hand it backs the files up great, with no issues.

Although, when it is run via cronjobs every hour, it seems to mess up badly. What happens is that it is supposed to zip the server, files, but instead of creating a 500 MB zip archive, it creates a file that is 7 MB and has random letters, like "zi2EEzFC" or "zi3Ad2sD". Everytime it is run automatically via cronjobs, it does this.

~Snipped~

---

### Post by squaregoldfish on 2011-12-16
Could you mark the thread as solved and describe your solution please? It will help others in the future who come here with a similar problem.

Thanks,
Steve.

---

