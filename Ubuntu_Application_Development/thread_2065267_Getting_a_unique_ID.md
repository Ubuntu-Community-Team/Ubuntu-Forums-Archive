---
title: "Getting a unique ID"
date: 2012-10-01
forum: Ubuntu Application Development
---

### Post by nigelenki on 2012-10-01
Here's one way to get a unique ID, bash:

```

unique_sequential_id() {
  local dplaces=${1-2}
  local j=$(date +%s.%N);
  local k=$(echo $j | cut -f1 -d'.');
  echo $(( k / 84600 )).$(( k % 86400 )).$(echo $j | cut -f2 -d'.' | cut -c 1-${dplaces})
}

```

Gives output:

(Days since Epoch).(Seconds since midnight).(Subseconds out to 10^-$dplaces)

These numbers are unique and sequential on a single system; don't use this for i.e. clustered CGI scripts.  You can go out to nanoseconds.

I found something in a CGI script here that used a non-critical counter to assign unique identifiers.  It works well under low load, but under high load I'd expect a race condition.  Essentially it selects a row containing an integer from a MySQL database, then increments that column.  Do this in parallel at just the right timing (= race condition) and you'll get 5 and 5 and then increment to 6 and 7 (MySQL lets you tell it update some_column = some_column+1).

By contrast, the above method includes a race condition where 'date' is called at the exact same nanosecond time on two different systems.  If you chose fewer decimal places, then it's safe to requests that complete within and are started less often than 10^-n seconds collision.

In other words, still not safe.

No real good way to do this without a lot of overhead, really.  Database select-and-increment is a lot more overhead than a shell script should have ;)

---

