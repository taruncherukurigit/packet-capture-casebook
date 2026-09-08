# Packet Capture Casebook

Four real packet captures, each tied to a specific bug or design decision from other projects in the [Cherwood Corporation](https://cherwood.tarunc.com) portfolio — not a tutorial series, evidence that I can actually read what's on the wire.

## Entries

| # | Capture | What it proves |
|---|---|---|
| 1 | [SSL-VPN TLS handshake](PACKET-CAPTURES.md#entry-1--ssl-vpn-tls-handshake--cipher-negotiation) | Cipher-hardening config confirmed live on the wire, plus a real internet scanner caught mid-handshake against the intentionally exposed portal |
| 2 | [HSRP failover cutover](PACKET-CAPTURES.md#entry-2--hsrp-hello-traffic--failover-cutover) | Measured failover time from real timestamps (3.33s) instead of a stopwatch estimate, plus the full troubleshooting trail (wrong capture point → SVI-down root cause → fix) |
| 3 | [LLDP discovery frames](PACKET-CAPTURES.md#entry-3--lldp-discovery-frames) | Raw TLVs matched against what `topology.py` actually parses, plus a verified explanation for why FortiGate's LLDP never crossed a SPAN capture |
| 4 | [Blocked DMZ→Trusted recon](PACKET-CAPTURES.md#entry-4--blocked-dmz--trusted-reconnaissance-attempt) | Segmentation enforcement proven at the packet level — request in, no reply, ever |

**Full writeup with timestamps, TLV breakdowns, screenshots, and the real troubleshooting story behind each capture: [PACKET-CAPTURES.md](PACKET-CAPTURES.md)**

## Repo structure

```
PACKET-CAPTURES.md              full writeup, screenshots embedded inline
captures/
  ssl-vpn-handshake.pcap        entry 1
  hsrp-failover-cutover.pcapng  entry 2 — the cutover itself
  hsrp-rejoin-recovery.pcapng   entry 2 — primary rejoining, no-preempt confirmed
  lldp-discovery-cisco.pcapng   entry 3
  dmz-recon-blocked.pcap        entry 4
screenshots/
  01-ssl-vpn/
  02-hsrp-failover/
  03-lldp/
  04-dmz-recon/
```

Open any `.pcap`/`.pcapng` in Wireshark. Screenshots are referenced inline in `PACKET-CAPTURES.md` so the full story renders directly on GitHub without opening a single capture file.

## Related projects

- [Cherwood Health](https://cherwood.tarunc.com) — SSL-VPN, DMZ segmentation
- HA/Failover Lab — HSRP
- [Cherwood Network Solutions](https://itsolutions.tarunc.com) — LLDP / Topology Discovery
