---
title: "nagios question"
date: 2010-10-27
forum: Server Platforms
---

### Post by newbie_css on 2010-10-27
i got a problem with my nagios monitoring 

i created host.cfg file for workstation monitoring. everything looks fine before the workstation re-connect the internet. 

to test if my new host monitoring works fine, i disconnect it from internet, and nagios highlight this workstation in red. so far so good.

but when i re-connect it to internet, the status on nagios remains in red. i try to restart the workstation, it is not working either. 

anyone know whts the problem is?

the following are the codes i wrote in the host.cfg

define host {
       host_name                  yuki           
       alias                      yuki
       address                    192.168.0.104     
       contact_groups             sagroup        
       check_command              check-host-alive    
       max_check_attempts         5
       notification_interval      10    
       notification_period        24x7
       notification_options       d,u,r
       }


define contactgroup {
        contactgroup_name    sagroup              
        alias                system administrator group
     
}


define service {
        host_name                 yuki            
        service_description       check-host-alive
        check_period              24x7
        max_check_attempts        4
        normal_check_interval     3
        retry_check_interval      2
        contact_groups            sagroup        
        notification_interval   10
        notification_period     24x7
        notification_options    w,u,c,r
        check_command           check-host-alive      
}

---

