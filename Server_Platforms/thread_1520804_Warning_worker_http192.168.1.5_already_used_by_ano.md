---
title: "Warning worker http://192.168.1.5/ already used by another worker"
date: 2010-06-30
forum: Server Platforms
---

### Post by tapas_mishra on 2010-06-30
I am having 2 websites running on a reverse proxy.
When ever I am restarting apache I am getting the warning

```

worker http://192.168.1.5/ already used by another worker

```

I googled it but could not reach any meaningful conclusion.

My vhost configuration which created above warning is
```


   ProxyPass / http://192.168.1.5/
    ProxyPassReverse / http://192.168.1.5/

      ProxyPass /website1 http://192.168.1.5/website1
       ProxyPassReverse /website1 http://192.168.1.5/website1

```

---

