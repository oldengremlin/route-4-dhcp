route-4-dhcp
============

Calculate Classless Route Option 121, [RFC 3442](https://tools.ietf.org/html/rfc3442), The Classless Static Route Option for Dynamic Host Configuration Protocol (DHCP) version 4

Classless Route Option Format
-----------------------------

The code for this option is 121, and its minimum length is 5 bytes.
 This option can contain one or more static routes, each of which consists of a destination descriptor and the IP address of the router that should be used to reach that destination.

     Code  Len Destination 1   Router 1
    +-----+---+----+-----+----+----+----+----+----+
    | 121 | n | d1 | ... | dN | r1 | r2 | r3 | r4 |
    +-----+---+----+-----+----+----+----+----+----+

     Destination 2        Router 2
    +----+-----+----+----+----+----+----+
    | d1 | ... | dN | r1 | r2 | r3 | r4 |
    +----+-----+----+----+----+----+----+

Sample use
----------

    $ rfc3442.route-4-dhcp.pl 10.0.0.0/8 192.168.88.2 172.16.0.0/12 192.168.88.2 192.168.0.0/16 192.168.88.2 0.0.0.0/0 192.168.88.1
    option_121_route_10.0.0.0/8_via_192.168.88.2 : 0x080ac0a85802
    option_249_route_10.0.0.0/8_via_192.168.88.2 : 0x080ac0a85802
    option_121_route_172.16.0.0/12_via_192.168.88.2 : 0x0cac10c0a85802
    option_249_route_172.16.0.0/12_via_192.168.88.2 : 0x0cac10c0a85802
    option_121_route_192.168.0.0/16_via_192.168.88.2 : 0x10c0a8c0a85802
    option_249_route_192.168.0.0/16_via_192.168.88.2 : 0x10c0a8c0a85802
    option_121_route_0.0.0.0/0_via_192.168.88.1 : 0x00c0a85801
    option_249_route_0.0.0.0/0_via_192.168.88.1 : 0x00c0a85801
    aggregate_opt_121 : 0x080ac0a858020cac10c0a8580210c0a8c0a8580200c0a85801
    aggregate_opt_249 : 0x080ac0a858020cac10c0a8580210c0a8c0a8580200c0a85801

See more http://oldengremlin.blogspot.com/2016/10/routeros-dhcp.html

