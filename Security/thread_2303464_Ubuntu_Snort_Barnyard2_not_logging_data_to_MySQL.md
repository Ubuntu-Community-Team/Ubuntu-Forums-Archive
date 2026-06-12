---
title: "Ubuntu Snort Barnyard2 not logging data to MySQL"
date: 2015-11-19
forum: Security
---

### Post by tharaka2 on 2015-11-19
I have install Snort and Barnyard2 on my Ubuntu PC and try to save Snort logs using Barnyard2.


During command execution, all logs files are generating. But Barnyard2 not logging data to mysql database.


For Barnyard2 I have execute below command, and it is display below out put. But it is not showing mysql database validate parameters.


[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=340b3faa53&view=fimg&th=1511ddfac64de0e2&attid=0.0.3&disp=emb&realattid=ii_1511dd2f70c176dd&attbid=ANGjdJ9gTwuNzp6C1Em2UdQPEsuRDbXcevQ7NFxQ8P3chlLuQOiAwB_39qUEb0NZkIAfHgaZ_nBjWwOVnn7cGE50r_XrgOCJ7M2QsLHTjNM24yaa_HJf1kYcDU6HBf4&sz=w1256-h204&ats=1447910185302&rm=1511ddfac64de0e2&zw&atsh=1[/IMG]




barnyard2.conf database configurations as below

output database: log, mysql, user=root password=abc123 dbname=snort host=localhost

My log file output are as below


[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=340b3faa53&view=fimg&th=1511ddfac64de0e2&attid=0.0.1&disp=emb&realattid=ii_1511dd50ea9a4025&attbid=ANGjdJ_Hw3AZXG3L2d0KB-WD50K0FLXX8pLP0D2iMyiVEd11eFqgf6hOmX-pKvBJWxtwxBG2JqSFFbOihVLQ0qumNNAvWiGgmMGY1FmgVlPnD_Jd5Xsco5yecLVQmio&sz=w1150-h146&ats=1447910185302&rm=1511ddfac64de0e2&zw&atsh=1[/IMG]



Database event table result


[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=340b3faa53&view=fimg&th=1511ddfac64de0e2&attid=0.0.2&disp=emb&realattid=ii_1511dd65c65bb254&attbid=ANGjdJ_-VCp6mlbuIyhBxEKNfW3HY-5hBGRbO7pfDRv7jU4AATbt_JXajzGJ-nGPJApx9qcR6Zxps-90IxmKXRZUiWPuHMLiHrKTxFaauxV6bRvLL1R9EYvpDDuvsec&sz=w944-h348&ats=1447910185302&rm=1511ddfac64de0e2&zw&atsh=1[/IMG]




For further referances, I have attached my snort.conf and barnyard2.conf files herewith. (ubuntu.zip)




Could you please analysis and let me know where is the issue and how can I fixed it !

---

