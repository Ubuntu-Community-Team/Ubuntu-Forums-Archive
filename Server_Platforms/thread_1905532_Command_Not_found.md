---
title: "Command Not found"
date: 2012-01-07
forum: Server Platforms
---

### Post by jeevandongre on 2012-01-07
I downloaded the AWS CloudWatch command line api and I have also set the env_path variable that is AWS_CLOUDWATCH_HOME=local/usr/CloudWatch. But when I run 'mon-cmd' I get command not found error in the console,I have working on ubuntu 10.04 server which is a EC2 instance.

Its been to couple of days I am struck with this problem, in spite of setting the path variables correctly I am facing this problem.

Kindly help me out

---

### Post by m_duck on 2012-01-07
I am not familiar with the program in question, but where is the 'mon-cmd' binary located? If it is not in one of the folders in your $PATH environment variable, you will have to either run it using its full path, add the path in question to your $PATH or change to the directory it is in, and run it with ./mon-cmd.

---

### Post by jeevandongre on 2012-01-07
I was able to find the solution for this problem, thanks for replying back.

---

