两种写法实现Session Scope的Spring Bean

来自网络

xml based:
```XML
<bean id="localRepository" class="com.demo.bean.LocalRepository" scope="session">
    <!-- To effects the proxying when used as dependencies by singleton beans. This requires CGLIB -->
    <aop:scoped-proxy />
</bean>
 
```

Java based:

```Java
@Component
@Scope(value = "session", proxyMode = ScopedProxyMode.TARGET_CLASS)
public class LocalRepository implements DisposableBean {
    // TODO  

    @Override
    public void destroy() throws Exception {
        // cleanup
    }
}

```

ScopeProxyMode.TARGET_CLASS means:

Create a class-based proxy (uses CGLIB).