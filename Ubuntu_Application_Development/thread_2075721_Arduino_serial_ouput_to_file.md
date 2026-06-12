---
title: "Arduino serial ouput to file?"
date: 2012-10-24
forum: Ubuntu Application Development
---

### Post by conradin on 2012-10-24
Hi all,
Yesterday I started using the Arduino. I'm happy at easy everything seems to be. What I haven't figured out yet is how to send the serial output to a file. The device is mounted at /dev/ttyACM0
```
void setup()                    
{
  Serial.begin(9600);              // set up Serial library at 9600 bps
  Serial.println("Hello world!");  // prints hello with ending line break 
}
void loop()                       
{
                                  // do nothing!
}
```
For example, how could I send that to a file on my computer?

---

### Post by rushikesh988 on 2012-10-24
i dnt know but may be u will have to write any kernal module ....why dnt u use putty may be it will have any option to write in file (but not sure)

---

### Post by conradin on 2012-10-24
I just tried:
```
#!/bin/bash
#http://www.yetanother.eu/arduino/articles/temp_basic.php 
# Port setting
stty -F /dev/ttyACM0 raw speed 9600
 
# Loop
while [ 1 ]; do
READ=`dd if=/dev/ttyACM0 count=1`
echo $READ >> filename
done
```
but the output is broken.
```
$ cat filename 
Hello world!
Hell
Hello
Hello wo

Hello w
Hello

```

for clarity, I changed my arduino code to:
```

void setup()                    
{
  Serial.begin(9600);              // set up Serial library at 9600 bps
}
void loop()                       
{
 delay(9000); 
 Serial.println("Hello world!");  // prints hello with ending line break 
}

```

so that I have a stream to read. 
I imagine I could write a server app and have it listen on a socket for the arduino. That strikes me as less easy but something which would work.
The problem with bash script above is its not listening, its just copying, its not waiting for data to get there, which is why I'm missing data. 

I assume this is a common task for arduino users so I'm just looking for the best ways to get it done. The end result will be to get sensor data from an areo-flexor Im going to build. But I need to figure out how to store data from that system first.

---

### Post by drdos2006 on 2012-10-24
This might help.

[http://www.easysw.com/~mike/serial/serial.html#2_5](http://www.easysw.com/~mike/serial/serial.html#2_5)

regards

---

### Post by rushikesh988 on 2012-11-05
try this>  stty raw ; cat > received.txt

---

