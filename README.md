Author: Joe Rizzo
********************

Converts a field with IP4 decimal format to a new field in the dotted-decimal address format.

Usage:
    <search containing field with decimal ip> | dec2ip <input field> <output field>

Example:
    | stats count | fields - count | eval dec="2046352469" | dec2ip dec ip

Based on:
    http://stackoverflow.com/questions/9590965/convert-an-ip-string-to-a-number-and-vice-versa
    ip2int = lambda ip: reduce(lambda a, b: (a << 8) + b, map(int, ip.split('.')), 0)
    int2ip = lambda n: '.'.join([str(n >> (i << 3) & 0xFF) for i in range(0, 4)[::-1]])
