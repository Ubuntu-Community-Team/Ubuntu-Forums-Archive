---
title: "Help test EC2 mirrors"
date: 2012-01-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by castrojo on 2012-01-11
Ubuntu now has mirrors hosted on EC2 on Amazon and we need people crushing them to find bugs. :) 

These are great because they're fast, and they update fast too so if your mirror is slow/broken or gets errors often, then you can give these a shot:

[http://cloud.ubuntu.com/2012/01/regional-s3-backed-ec2-mirrors-available-for-testing/](http://cloud.ubuntu.com/2012/01/regional-s3-backed-ec2-mirrors-available-for-testing/)

Here's mine for an example: 

deb [http://us-east-1.ec2.archive.ubuntu.com.s3.amazonaws.com/ubuntu](http://us-east-1.ec2.archive.ubuntu.com.s3.amazonaws.com/ubuntu) precise main restricted universe multiverse

You can set the region based on where you are in the world according to this list: [http://docs.amazonwebservices.com/general/latest/gr/rande.html#ec2_region](http://docs.amazonwebservices.com/general/latest/gr/rande.html#ec2_region)

So replace the "us-east-1" in that line with the part from h:

US East (Northern Virginia) Region	us-east-1
US West (Oregon) Region	ec2.us-west-2.amazonaws.com
US West (Northern California) Region	us-west-1
EU (Ireland) Region	eu-west-1
Asia Pacific (Singapore) Region	ap-southeast-1
Asia Pacific (Tokyo) Region	ap-northeast-1
South America (Sao Paulo) Region	sa-east-1

---

