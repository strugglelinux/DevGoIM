##自己动手开发IM

数据传输格式考虑方面：

1、网络数据大小：占用带宽，传输效率
    虽然对单个用户来说，数据量传输很小，但是对于服务器端要承受众多的高并发数据传输（尤其现时高并发、大用户量的IM聊天应用和实时推送服务端等场景），必须要考虑到数据占用带宽，尽量不要有冗余数据，这样才能够少占用带宽，少占用资源，少网络IO，提高传输效率。

2、网络数据安全性：敏感数据的网络安全
    对于相关业务的部分数据传输都是敏感数据，所以必须考虑对部分传输数据进行加密。这通常出现在银行等数据安全性要求很高的应用行业和场景里，当然传统的即时通讯应用里基于用户隐私考虑，数据加密也是同样是个必须考虑的问题。安全性是应用的基础条件，需求是一样的，只是加密程度、安全性级别要求有不同而已。

3、编码复杂度
    编码复杂度包括序列化和反序列化复杂度、效率、数据结构的可扩展性和可维护性。
    对于平台相关业务的代码实现也需要考虑到数据发送方和数据接收方数据处理的复杂度和数据结构的可扩展性，可维护性，人力成本和实施复杂度也必须考虑在内。通常情况下，即时通讯应用（比如IM聊天应用）在开发的前期，为了方便调试，很多团队会用简单的文本协议、JSON等能直观查看的方式，但后期生产部署后，为了流量等考虑，可能会转用Protobuf等更省流量的协议。但总之，协议的定义不可能永远一成不变，但如果在实现的时候就有这些预见性，相性会大大减轻未来的运营风险。

4、协议通用性、大众规范
    数据类型必须是跨平台，数据格式是通用的，大家普遍能接受上手的。当然，现在已经迈入移动互联网时代，多端、多平台、异构平台的数据通讯是先决条件，而协议的选择，通用性也最多只是应用层有区别。当然，无论如何，异构平台的一致性，是毫无争议的必备条件。


数据传输格式选型：Protobuf、json
