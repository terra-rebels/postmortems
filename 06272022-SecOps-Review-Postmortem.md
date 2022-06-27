# SecOps review of Terra Classic code base

## Summary

The following postmortum outlines HIGH severity vulnerabilities across the main components of the terra code base that are considered a priority to fix. It is understood that most of these problems are based on upstream dependencies and it might not always be possible or beneficial to do so. This however does not remove the need to provide transparence about where potential future attacks could come from and how we can potentially guard against it.


## Timeline

| Time | Event |
| --- | --- |
| 2022-06-27 | (CVE-2022-25878) https://security.snyk.io/vuln/SNYK-JS-PROTOBUFJS-2441248 identified in terra.proto repository |
| 2022-06-27 | (CVE-2022-25878) https://security.snyk.io/vuln/SNYK-JS-PROTOBUFJS-2441248 identified in msg-reader repository |
| 2022-06-27 | (CWE-327) Use of a Broken or Risky Cryptographic Algorithm in oracle-feeder repository |
| 2022-06-27 | (CVE-2021-3807) https://security.snyk.io/vuln/SNYK-JS-ANSIREGEX-1583908 identified in ledger-terra-js repository |
| 2022-06-27 | (CVE-2021-3807) https://security.snyk.io/vuln/SNYK-JS-ANSIREGEX-1583908 identified in station-extension repository |
| 2022-06-27 | (CVE-2021-3807) https://security.snyk.io/vuln/SNYK-JS-ANSIREGEX-1583908 identified in station repository |
| 2022-06-27 | (CVE-2020-9283) https://app.snyk.io/vuln/SNYK-GOLANG-GOLANGORGXCRYPTOSSH-551923 identified in classic-core repository |
| 2022-06-27 | (CVE-2019-20933) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMINFLUXDATAINFLUXDBSERVICESHTTPD-1041719 identified in classic-core repository |
| 2022-06-27 | (CVE-2020-14040) https://security.snyk.io/vuln/SNYK-GOLANG-GOLANGORGXTEXTENCODINGUNICODE-609611 identified in classic-core repository |
| 2022-06-27 | (CVE-2022-28948) https://security.snyk.io/vuln/SNYK-GOLANG-GOPKGINYAMLV3-2841557 identified in classic-core repository |
| 2022-06-27 | (CVE-2020-15114) https://security.snyk.io/vuln/SNYK-GOLANG-GOETCDIOETCDV3ETCDMAIN-1083901 identified in classic-core repository |
| 2022-06-27 | (CVE-2020-26160) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMDGRIJALVAJWTGO-596515 identified in classic-core repository |
| 2022-06-27 | (CVE-2022-23327) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMETHEREUMGOETHEREUMCORE-2419061 identified in classic-core repository |
| 2022-06-27 | (CVE-2021-42219) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMETHEREUMGOETHEREUMCONSENSUSETHASH-2428324 identified in classic-core repository |
| 2022-06-27 | (CVE-2021-43668) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMETHEREUMGOETHEREUMCMDGETH-1923106 identified in classic-core repository |
| 2022-06-27 | (CVE-2021-41173) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMETHEREUMGOETHEREUMCMDGETH-1767102 identified in classic-core repository |
| 2022-06-27 | (CVE-2020-27813) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMGORILLAWEBSOCKET-597108 identified in classic-core repository |
| 2022-06-27 | (CVE-2020-28466) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMNATSIONATSSERVERV2SERVER-1083984 identified in classic-core repository |
| 2022-06-27 | (CVE-2021-30465) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMOPENCONTAINERSRUNCLIBCONTAINER-1294545 identified in classic-core repository |
| 2022-06-27 | (CVE-2021-42836) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMTIDWALLGJSON-1766963 identified in classic-core repository |
| 2022-06-27 | (CVE-2020-29652) https://security.snyk.io/vuln/SNYK-GOLANG-GOLANGORGXCRYPTO-2825234 identified in classic-core repository |
| 2022-06-27 | (CVE-2021-44716) https://security.snyk.io/vuln/SNYK-GOLANG-GOLANGORGXNETHTTP2-2313688 identified in classic-core repository |
| 2022-06-27 | (CWE-400) https://security.snyk.io/vuln/SNYK-GOLANG-NHOOYRIOWEBSOCKET-1244972 identified in classic-core repository |
| 2022-06-27 | (CVE-2019-19794) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMMIEKGDNS-537825 identified in classic-core repository |
| 2022-06-27 | (CVE-2021-43784) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMOPENCONTAINERSRUNCLIBCONTAINER-2309909 identified in classic-core repository |
| 2022-06-27 | (CVE-2020-28483) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMGINGONICGIN-1041736 identified in classic-core repository |
| 2022-06-27 | (CWE-79) https://cwe.mitre.org/data/definitions/79.html identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2020-9283) https://app.snyk.io/vuln/SNYK-GOLANG-GOLANGORGXCRYPTOSSH-551923 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2022-26945) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMHASHICORPGOGETTER-2421223 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2022-28948) https://security.snyk.io/vuln/SNYK-GOLANG-GOPKGINYAMLV3-2841557 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-29482) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMULIKUNITZXZ-607912 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2020-16845) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMULIKUNITZXZ-598892 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2020-29652) https://security.snyk.io/vuln/SNYK-GOLANG-GOLANGORGXCRYPTO-2825234 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-44716) https://security.snyk.io/vuln/SNYK-GOLANG-GOLANGORGXNETHTTP2-2313688 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2022-30322) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMHASHICORPGOGETTER-2847926 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2022-30323) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMHASHICORPGOGETTER-2847925 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2022-30321) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMHASHICORPGOGETTER-2847924 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2019-20933) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMINFLUXDATAINFLUXDBSERVICESHTTPD-1041719 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2020-26160) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMDGRIJALVAJWTGO-596515 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2022-23327) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMETHEREUMGOETHEREUMCORE-2419061 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-42219) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMETHEREUMGOETHEREUMCONSENSUSETHASH-2428324 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2020-28466) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMNATSIONATSSERVERV2SERVER-1083984 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-30465) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMOPENCONTAINERSRUNCLIBCONTAINER-1294545 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-42836) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMTIDWALLGJSON-1766963 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2019-19794) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMMIEKGDNS-537825 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2020-28483) https://security.snyk.io/vuln/SNYK-GOLANG-GITHUBCOMGINGONICGIN-1041736 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2022-0691) https://security.snyk.io/vuln/SNYK-JS-URLPARSE-2407770 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-23424) https://security.snyk.io/vuln/SNYK-JS-ANSIHTML-1296849 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-3807) https://security.snyk.io/vuln/SNYK-JS-ANSIREGEX-1583908 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-43138) https://security.snyk.io/vuln/SNYK-JS-ASYNC-2441827 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-3749) https://security.snyk.io/vuln/SNYK-JS-AXIOS-1579269 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-3803) https://security.snyk.io/vuln/SNYK-JS-NTHCHECK-1586032 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-23337) https://security.snyk.io/vuln/SNYK-JS-LODASHTEMPLATE-1088054 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-3918) https://security.snyk.io/vuln/SNYK-JS-JSONSCHEMA-1920922 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2021-33502) https://security.snyk.io/vuln/SNYK-JS-NORMALIZEURL-1296539 identified in cosmos-sdk repository |
| 2022-06-27 | (CWE-1321) https://security.snyk.io/vuln/SNYK-JS-UNSETVALUE-2400660 identified in cosmos-sdk repository |
| 2022-06-27 | (CVE-2022-24772) https://security.snyk.io/vuln/SNYK-JS-NODEFORGE-2430339 identified in cosmos-sdk repository |


## Contributing Factors

- Upstream dependencies
- More upstream dependencies
- You guessed it, even more upstream dependencies


## Lessons Learned

- Always vet your 3rd party dependencies
- Understand your software supply chain and its vulnerabilities @ https://github.com/dfds/dojo/tree/master/handouts/supply-chain-attacks


## Action Items

- Patch CVE-2022-25878 in terra.proto repository by upgrading to protobufjs@6.11.3
- Patch CVE-2022-25878 in msg-reader repository by upgrading to protobufjs@6.11.3
- Patch CWE-327 by upgrading Cryptographic Algorithm in oracle-feeder repository
- Patch CVE-2021-3807 by upgrading to ansi-regex@6.0.1 in ledger-terra-js repository
- Patch CVE-2021-3807 by upgrading to ansi-regex@6.0.1 in station-extension repository
- Patch CVE-2021-3807 by upgrading to ansi-regex@6.0.1 in station repository
- Patch CVE-2020-9283 by upgrading to golang.org/x/crypto@0.0.0-20200220183623-bac4c82f6975 in classic-core repository
- Patch CVE-2020-9283 by upgrading to github.com/influxdata/influxdb@1.7.6 in classic-core repository
- Patch CVE-2020-14040 by upgrading to golang.org/x/text@0.3.3 in classic-core repository
- Patch CVE-2022-28948 by upgrading to gopkg.in/yaml.v3@3.0.0 in classic-core repository
- Patch CVE-2020-15114 by upgrading to go.etcd.io/etcd@3.4.10 in classic-core repository
- Patch CVE-2020-26160 by upgrading to github.com/dgrijalva/jwt-go@4.0.0-preview1 in classic-core repository
- Patch CVE-2022-23327 by upgrading to github.com/ethereum/go-ethereum@1.10.13 in classic-core repository
- Patch CVE-2021-41173 by upgrading to github.com/ethereum/go-ethereum@1.10.9 in classic-core repository
- Patch CVE-2020-2781 by upgrading to github.com/gorilla/websocket@1.4.1 in classic-core repository
- Patch CVE-2020-28466 by upgrading to github.com/nats-io/nats-server@2.2.0 in classic-core repository
- Patch CVE-2021-30465 by upgrading to github.com/opencontainers/runc@1.0.0-rc95 in classic-core repository
- Patch CVE-2021-42836 by upgrading to github.com/tidwall/gjson@1.9.3 in classic-core repository
- Patch CVE-2020-29652 by upgrading to golang.org/x/crypto@0.0.0-20201216223049-8b5274cf687f in classic-core repository
- Patch CVE-2021-44716 by upgrading to golang.org/x/net@0.0.0-20211209124913-491a49abca63 in classic-core repository
- Patch CWE-400 by upgrading to nhooyr.io/websocket@1.8.7 in classic-core repository
- Patch CVE-2019-19794 by upgrading to github.com/miekg/dns@1.1.25 in classic-core repository
- Patch CVE-2021-43784 by upgrading to github.com/opencontainers/runc@1.0.3 in classic-core repository
- Patch CVE-2020-28483 by upgrading to github.com/gin-gonic/gin@1.7.7 in classic-core repository
- Patch CVE-2020-9283 by golang.org/x/crypto@0.0.0-20200220183623-bac4c82f6975 in cosmos-sdk repository
- Patch CVE-2022-26945 by github.com/hashicorp/go-getter@2.1.0 in cosmos-sdk repository
- Patch CVE-2022-28948 by gopkg.in/yaml.v3@3.0.0 in cosmos-sdk repository
- Patch CVE-2021-29482 by github.com/ulikunitz/xz@0.5.8 in cosmos-sdk repository
- Patch CVE-2020-16845 by github.com/ulikunitz/xz@0.5.8 in cosmos-sdk repository
- Patch CVE-2020-29652 by upgrading to golang.org/x/crypto@0.0.0-20201216223049-8b5274cf687f in cosmos-sdk repository
- Patch CVE-2021-44716 by upgrading to golang.org/x/net@0.0.0-20211209124913-491a49abca63 in cosmos-sdk repository
- Patch CVE-2022-30322 by upgrading to github.com/hashicorp/go-getter@2.1.0 in cosmos-sdk repository
- Patch CVE-2022-30323 by upgrading to github.com/hashicorp/go-getter@2.1.0 in cosmos-sdk repository
- Patch CVE-2022-30321 by upgrading to github.com/hashicorp/go-getter@2.1.0 in cosmos-sdk repository
- Patch CVE-2019-20933 by upgrading to github.com/influxdata/influxdb@1.7.6 in cosmos-sdk repository
- Patch CVE-2020-26160 by upgrading to github.com/dgrijalva/jwt-go@4.0.0-preview1 in cosmos-sdk repository
- Patch CVE-2022-23327 by upgrading to github.com/ethereum/go-ethereum@1.10.13 in cosmos-sdk repository
- Patch CVE-2020-28466 by upgrading to github.com/nats-io/nats-server@2.2.0 in cosmos-sdk repository
- Patch CVE-2021-30465 by upgrading to github.com/opencontainers/runc@1.0.0-rc95 in cosmos-sdk repository
- Patch CVE-2021-42836 by upgrading to github.com/tidwall/gjson@1.9.3 in cosmos-sdk repository
- Patch CVE-2019-19794 by github.com/miekg/dns@1.1.25 in cosmos-sdk repository
- Patch CVE-2020-28483 by upgrading to github.com/gin-gonic/gin@1.7.7 in cosmos-sdk repository
- Patch CVE-2022-0691 by upgrading to url-parse@1.5.9 in cosmos-sdk repository
- Patch CVE-2021-23424 by upgrading to ansi-html@0.0.9 in cosmos-sdk repository
- Patch CVE-2021-3807 by upgrading to ansi-regex@6.0.1 in cosmos-sdk repository
- Patch CVE-2021-43138 by upgrading to async@3.2.2 in cosmos-sdk repository
- Patch CVE-2021-3749 by upgrading to axios@0.21.3 in cosmos-sdk repository
- Patch CVE-2021-3803 by upgrading to prismjs@1.25.0 in cosmos-sdk repository
- Patch CVE-2021-3918 by upgrading to json-schema@0.4.0 in cosmos-sdk repository
- Patch CVE-2021-33502 by upgrading to normalize-url@6.0.1 in cosmos-sdk repository
- Patch CWE-1321 by upgrading to unset-value@2.0.1 in cosmos-sdk repository
- Patch CVE-2022-24772 by upgrading to node-forge@1.3.0 in cosmos-sdk repository
