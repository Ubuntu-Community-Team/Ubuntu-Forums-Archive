---
title: "Apache overload on port 80 on 8080 not Why?"
date: 2009-11-18
forum: Server Platforms
---

### Post by Abadon_ on 2009-11-18
Hello,

My OS is Ubuntu Hardy, Kernel 2.6.24-25-virtual, VMware tools the last version, the host machine is a VMware ESX 4 with processors Intel (R) Xeon (R) CPU E5405@2.00GHz. For my virtual machine are allocated 256MB of RAM, restricted to use up to 450 Mhz processor during a Xeon and I have a 100Mbit-flat channel to the Internet. My problem is the following when I decide to test the performance of Apacha and from my laptop run ab -c 10 -n 1000 [http://mysite.com/](http://mysite.com/) and receive this:
> This is ApacheBench, Version 2.3 <$Revision: 655654 $>                    
Copyright 1996 Adam Twiss, Zeus Technology Ltd, [http://www.zeustech.net/](http://www.zeustech.net/)  
Licensed to The Apache Software Foundation, [http://www.apache.org/](http://www.apache.org/)        

Benchmarking mysite.com (be patient)
Completed 100 requests                        
Completed 200 requests                        
Completed 300 requests                        
Completed 400 requests                        
Completed 500 requests                        
Completed 600 requests                        
Completed 700 requests                        
Completed 800 requests                        
Completed 900 requests                        
Completed 1000 requests                       
Finished 1000 requests                        


Server Software:        Apache
Server Hostname:        mysite.com
Server Port:            80                  

Document Path:          /
Document Length:        39066 bytes

Concurrency Level:      10
Time taken for tests:   269.738 seconds
Complete requests:      1000           
Failed requests:        0              
Write errors:           0              
Total transferred:      39434000 bytes 
HTML transferred:       39066000 bytes 
Requests per second:    3.71 [#/sec] (mean)
Time per request:       2697.376 [ms] (mean)
Time per request:       269.738 [ms] (mean, across all concurrent requests)
Transfer rate:          142.77 [Kbytes/sec] received                       

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        1    7  60.6      1     636
Processing:    50 2685 890.6   2750   10954
Waiting:       46 2659 892.9   2718   10949
Total:         51 2692 890.8   2757   10955

Percentage of the requests served within a certain time (ms)
  50%   2757                                                
  66%   2925                                                
  75%   2957                                                
  80%   2974                                                
  90%   3018                                                
  95%   3061                                                
  98%   3533                                                
  99%   4029                                                
 100%  10955 (longest request)    

When I change port from 80 to 8080 and test again ab -c 10 -n 1000 [http://mysite.com:8080/](http://mysite.com:8080/) and receive:
> This is ApacheBench, Version 2.3 <$Revision: 655654 $>             
Copyright 1996 Adam Twiss, Zeus Technology Ltd, [http://www.zeustech.net/](http://www.zeustech.net/)
Licensed to The Apache Software Foundation, [http://www.apache.org/](http://www.apache.org/)      

Benchmarking mysite.com (be patient)
Completed 100 requests                        
Completed 200 requests                        
Completed 300 requests                        
Completed 400 requests                        
Completed 500 requests                        
Completed 600 requests                        
Completed 700 requests                        
Completed 800 requests                        
Completed 900 requests                        
Completed 1000 requests                       
Finished 1000 requests                        


Server Software:        Apache
Server Hostname:        mysite.com
Server Port:            8080                

Document Path:          /
Document Length:        0 bytes

Concurrency Level:      10
Time taken for tests:   19.362 seconds
Complete requests:      1000          
Failed requests:        0             
Write errors:           0             
Non-2xx responses:      1000          
Total transferred:      214000 bytes
HTML transferred:       0 bytes
Requests per second:    51.65 [#/sec] (mean)
Time per request:       193.620 [ms] (mean)
Time per request:       19.362 [ms] (mean, across all concurrent requests)
Transfer rate:          10.79 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        1    6  51.9      1     641
Processing:    14  188 265.8     42    1574
Waiting:       14  188 265.7     41    1574
Total:         15  194 268.6     43    1576

Percentage of the requests served within a certain time (ms)
  50%     43
  66%     48
  75%    153
  80%    609
  90%    668
  95%    682
  98%    695
  99%    722
 100%   1576 (longest request)
 

I can not explain why my performance fall so dramatically when Apache works on the port 80. Any suggestions ?

---

### Post by gombadi on 2009-11-18
> 
Document Length: 39066 bytes
Total transferred: 39434000 bytes
HTML transferred: 39066000 bytes 


And

> 
Document Length: 0 bytes
Total transferred: 214000 bytes
HTML transferred: 0 bytes


I don't think you are testing the same thing on the different ports. Looks like port 8080 is only returning an error message.

---

### Post by Abadon_ on 2009-11-19
My mistake. I had not seen this. Thanks.

---

