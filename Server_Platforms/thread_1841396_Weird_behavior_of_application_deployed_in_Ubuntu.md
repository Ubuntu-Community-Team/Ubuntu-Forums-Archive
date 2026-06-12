---
title: "Weird behavior of application deployed in Ubuntu"
date: 2011-09-09
forum: Server Platforms
---

### Post by user2901 on 2011-09-09
One application is running on ubuntu system. A particular request of the application is taking more than 2 minutes of time to finish. But I have seen  the same request is getting initiated automatically every after 2 minutes only in that particular ubuntu system. At first I felt,  the issue could be either in  the application or the application server or in that particular system network of the ubuntu system. So I have followed the below steps.
 
•         I have installed Fidder2 Debugger Proxy in my the local machine from where I am accessing the application. Here I could not see more than one log of the raised request.
 
•         I have deployed another application in the same ubuntu machine and added a never ending loop in a particular request  for the testing purpose. But I have seen the same type of behavior for that application also. The same request is initiated every after 2 minutes.
 
 
•         I have installed the same application in another Ubuntu systems and a windows system. The application server also is same here. But I have not seen this issue in those machines. 
 
So, I feel there could be any specific configuration present in that Ubuntu system network/in the system, which is initiating the incoming request in every 2 minutes if it doesn't send back the response. 

Please help me. If there is any way I can test whether the incoming request is initiated by the cache of the ubuntu or the remote system.

Thanks,
Raj

---

