---
title: "Ubuntu cloud help"
date: 2011-05-12
forum: Server Platforms
---

### Post by kaoskater08 on 2011-05-12
Hello all, 

I'm trying to install the Ubuntu cloud on a couple of computers and have come to a brick wall I can't figure out. When I run the command $ euca-describe-availability-zones verbose, I get the following: 

$ euca-describe-availability-zones verbose
AVAILABILITYZONE    cluster1    130.184.104.144
AVAILABILITYZONE    |- vm types    free / max   cpu   ram  disk
AVAILABILITYZONE    |- m1.small    0000 / 0000   1    192     2
AVAILABILITYZONE    |- c1.medium    0000 / 0000   1    256     5
AVAILABILITYZONE    |- m1.large    0000 / 0000   2    512    10
AVAILABILITYZONE    |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE    |- c1.xlarge    0000 / 0000   4   2048    20

I've tried syncing them by running this: $ sudo euca_conf --no-rsync --discover-nodes....and I get the following: 

New node found on fe80::21a:a0ff:fe18:761f; add it? [Yn] y

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.


Trying scp to sync keys to: eucalyptus@fe80::21a:a0ff:fe18:761f://var/lib/eucalyptus/keys/...
ssh: Could not resolve hostname fe80: Name or service not known
lost connection
failed.

ERROR: could not synchronize keys with fe80::21a:a0ff:fe18:761f!
The configuration will not have this node.
Hint: to setup passwordless login to the nodes as user eucalyptus, you can
run the following commands on node fe80::21a:a0ff:fe18:761f:
sudo -u eucalyptus mkdir -p ~eucalyptus/.ssh
sudo -u eucalyptus tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC4QPmQ/JjF4rm8u7kl14DxxKpz2vMD1BhJ6MbDJGy5LUqaJ0e0ddCUjXWabShOIhTJpwwueTSrnIgqtAMrkZg7Ca8Nj+rP+jZKf9SHsJlsBvFUkmDk7Aj1+nWzsleSZmLv2n6rrihuTtK5jT57zZxLf/UhBTUG2IOXTNcojrfgQvBFIMUVu/x7hyKQk+FS7YVnKI3L+9jqM1TBgDHlYEUKBhbcJrN57n7y0JkkZGpF45cD1IfQ9BRoifJ15awKx7+EArabDZSqmSXwDGJp8n4VJ8HHC8xMmjizZ073msEJ8nZlpwR8K9VvsjGIiWsGD//MpY1KMnBKmdeir1UQONbL eucalyptus@ubuntuCloudHost
EOT

Be sure that authorized_keys is not group/world readable or writable


Please help!!

---

