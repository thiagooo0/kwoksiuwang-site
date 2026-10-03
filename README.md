# kwoksiuwang.com

Static developer site, served by GitHub Pages at the apex domain `kwoksiuwang.com`.

| Path | Purpose |
|---|---|
| `/` | Developer home (App Store "Marketing URL" / ad-network "Website") |
| `/whitebear/` | White Bear Cafe support page (App Store "Support URL") |
| `/whitebear/privacy.html` | White Bear Cafe privacy policy (App Store "Privacy Policy URL") |
| `/app-ads.txt` | Authorised ad sellers. Must stay at the **apex** domain root |

No build step: plain HTML + one stylesheet.

## Deploy (GitHub Pages)

1. Push this folder to a public GitHub repo.
2. Repo › Settings › Pages › Source: *Deploy from a branch*, branch `main`, folder `/`.
3. Custom domain: `kwoksiuwang.com` (the `CNAME` file already holds it). Tick *Enforce HTTPS* once the certificate is issued.
4. Recommended: GitHub › Settings › Pages › *Verified domains* — add `kwoksiuwang.com` so no one else can claim it.

## DNS (DNSPod)

Only add records for the apex (`@`) and `www`. **Do not touch `v` and `sg`** — those are the VPN nodes.

| Host | Type | Value |
|---|---|---|
| `@` | A | `185.199.108.153` |
| `@` | A | `185.199.109.153` |
| `@` | A | `185.199.110.153` |
| `@` | A | `185.199.111.153` |
| `@` | AAAA | `2606:50c0:8000::153` |
| `@` | AAAA | `2606:50c0:8001::153` |
| `@` | AAAA | `2606:50c0:8002::153` |
| `@` | AAAA | `2606:50c0:8003::153` |
| `www` | CNAME | `<github-user>.github.io` |

Check (use a public resolver; a local proxy may return fake 198.18.x.x addresses):

```bash
curl -s "https://dns.google/resolve?name=kwoksiuwang.com&type=A"
```

## app-ads.txt

Holds the AdMob publisher line. When an ad network is added (e.g. through AdMob mediation), copy the line its dashboard gives you here and update the privacy policy.
