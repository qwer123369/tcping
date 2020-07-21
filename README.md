# Introduction

Tcping is ping probe command line tool, supporting ICMP, TCP and HTTP protocols.

You can also use it to query IP information from [https://ifconfig.is](https://ifconfig.is).

# Features

- Support ICMP/TCP/HTTP protocols
- Query basic IP information

# Installation

1. Download latest [release](https://github.com/i3h/tcping/releases/latest) (recommend)

2. Use go get

```
go get -u github.com/i3h/tcping
```

3. Build on your own

```
git clone https://github.com/i3h/tcping.git
cd tcping
go build
```

# Usage

```
  -h string
        HTTP Ping
  -i string
        ICMP Ping
  -m string
        MTR Trace
  -q string
        Query ip information
  -t string
        TCP Ping
  -v    Version
```

# Examples

```
$ tcping -h https://www.google.com
Proxy     :    false
Scheme    :    https
Host      :    www.google.com
DNS Lookup:    2.05 ms
TCP       :    2.41 ms
TLS       :    68.92 ms
Process   :    29.28 ms
Transfer  :    0.19 ms
Total     :    103.06 ms
```

```
$ tcping -i www.google.com
ICMP   OPEN      74.125.200.147    2.2 ms
```

```
$ tcping -t www.google.com:443
TCP    OPEN      www.google.com:443
```

```
$ tcping -q www.google.com
IP     :    172.217.194.103
City   :    Queenstown Estate
Country:    Singapore
ISP    :    Google LLC
AS     :    AS15169 Google LLC
```

# Note

Root permission is required when running ICMP ping, since it needs to open raw socket.

You can either use sudo command, or set setuid bit for tcping.

```
// Use sudo for one-time ping
$ sudo tcping -i google.com

// Set setuid bit
$ sudo chown root:root tcping
$ sudo chmod u+s tcping

```

# License

See the [LICENSE](https://github.com/i3h/tcping/blob/master/LICENSE.md) file for license rights and limitations (MIT).

# Acknowledgements

[lmas/icmp_ping.go](https://gist.github.com/lmas/c13d1c9de3b2224f9c26435eb56e6ef3)

[sparrc/go-ping](https://github.com/sparrc/go-ping)

[davecheney/httpstat](https://github.com/davecheney/httpstat)
