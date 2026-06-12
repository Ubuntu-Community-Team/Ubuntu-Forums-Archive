---
title: "Where is my template.js file in LimeSurvey?"
date: 2012-09-05
forum: Server Platforms
---

### Post by js9 on 2012-09-05
Dear fellow Limesurvey users/admins,

I'm following the steps on 
 [http://docs.limesurvey.org/tiki-index.php?page=Workarounds%3A+Manipulating+a+survey+at+runtime+using+Javascript&structure=English+Instructions+for+LimeSurvey#Variable_Length_Array_Multi_Flexible_Text_question](http://docs.limesurvey.org/tiki-index.php?page=Workarounds%3A+Manipulating+a+survey+at+runtime+using+Javascript&structure=English+Instructions+for+LimeSurvey#Variable_Length_Array_Multi_Flexible_Text_question). 
I've completed step 1. Step 2 is "Add the following script to your template.js file." 

I tried looking for my template.js file on my /limesurvey/ folder and subfolders on my website, using filezilla. But I can't seem to be able to locate the file. 

Where is it?

Thank you.

---

### Post by Habitual on 2012-09-05
js9:


ssh into your godaddy account and run this:
```
cd html/limesurvey
find -name template.js -type f
```

HTH.

---

