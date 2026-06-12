---
title: "After PAM Success help (c or c++)"
date: 2012-07-03
forum: Security
---

### Post by Spudd on 2012-07-03
So I have...
[PHP]#include <security/pam_appl.h>
#include <security/pam_misc.h>
#include <stdio.h>

int main(int argc, char** argv)
{
   if (argc < 2) {
      fprintf(stderr, "Usage: %s <username>\n", argv[0]);
      return 1;
   }

   const char*            user = argv[1];
   static struct pam_conv pam_conversation = { misc_conv, NULL };
   pam_handle_t*          pamh;

   int res = pam_start(argv[0], user, &pam_conversation, &pamh);

   if (res == PAM_SUCCESS) {
      res = pam_authenticate(pamh, 0);
   }

   if (res == PAM_SUCCESS) {
      res = pam_acct_mgmt(pamh, 0);
   }

   if (res == PAM_SUCCESS) {
      fprintf(stdout, "Authenticated.\n");
	system("whoami");
   }
   else {
      fprintf(stdout, "Not Authenticated.\n");
   }

   pam_end(pamh, res);

   return res == PAM_SUCCESS ? 0 : 1;
}[/PHP]
When my program gets to 'system("whoami");' it returns the user who ran the program. My goal is to spawn a new process of some program that is ran by the authenticated user. Thanks in advance.

---

### Post by Spudd on 2012-07-04
bump

---

### Post by Doug S on 2012-07-05
I don't have those pam includes on my computer, so I was unable to try your program towards trying to reply with a good suggestion. However, I was wondering (without testing it myself) if you would want to be using the setuid, setgid, seteuid function calls to achieve what you want.

---

### Post by Spudd on 2012-07-06
Those libraries are easy to install if you want, anyways I'm not familiar with that could you give me an example of it that works with Pam. If anyone else has another suggestion that may be the more common way PAM aware apps work. Thanks all.

---

