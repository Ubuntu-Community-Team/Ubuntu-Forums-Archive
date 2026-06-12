---
title: "Services using mono fail to start"
date: 2009-12-22
forum: Server Platforms
---

### Post by Kynto on 2009-12-22
Hi,

I am having abit of a problem using a mono service on startup, i have setup my init.d file and also added it to the startup list using update-rc.d, although my service does not appear to start, i have tested this with other applications so i am sure that my file is ok.

```

#!/bin/bash

### BEGIN INIT INFO
# Provides:       kynto
# Required-Start:    $local_fs $remote_fs $network $syslog
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Description: Start/stop Kynto Server
### END INIT INFO

case $1 in
    start)
        start-stop-daemon --start --exec /usr/bin/mono /home/KyntoServer/NewKyntoServer.exe
    ;;    
    stop)
        
        #todo
    ;;
    restart)
        
        #todo
    ;;
    *)
        echo "Usage: /etc/init.d/kynto {start|stop|restart}"
        exit 1
    ;;
esac

exit 1

```

Although if i run this when i login using ssh, it runs fine - which is very unusual (/etc/init.d/kynto start) although once i close the ssh session the server closes as well.

I am unsure of the problem, if anyone could help me this with that would be great!

thanks in advance,
Matt.

---

### Post by Kynto on 2009-12-23
I am still having this issue, i am not sure weather i am starting the service correctly, as if i run "/etc/init.d/kynto start" the service stops once i close the ssh session.

---

