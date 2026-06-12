---
title: "MySQL Error: Function Does Not Exist"
date: 2012-08-17
forum: Server Platforms
---

### Post by icKohen on 2012-08-17
Hello everyone,

I am in the process of moving one of my websites from Centos OS to Ubuntu 12.04. I haven't had any issues with Wordpress or vBulletin, but my custom built website is giving me very strange database query errors: 

> query failed !SELECT product_model.*,product_detail.product_name,product_detail.product_thumb,DATE_FORMAT(product_model_add_date ,'%m/%d/%Y')as product_model_add_date,device_model.model_name FROM product_detail inner join product_model on product_detail.product_id=product_model.product_id inner join device_model on product_model.device_model_id=device_model.device_model_id WHERE (product_model.device_model_id ='183' or supportsChildDevice(product_model.product_model_id,183) ) AND product_status=1 and status=1 ORDER BY product_model_id DESC:FUNCTION web_elecite.supportsChildDevice does not existquery failed 

Funny thing is, it works perfectly OK on Centos but not on Ubuntu. I have spent a bit of time on Google trying to find a reason for this and it seems like it has to do with the initial location of mysql on Centos in comparison to Ubuntu. I wasn't successful in finding a solution.

Any suggestions?

Thank you.

---

