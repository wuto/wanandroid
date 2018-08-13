# wanandroid
基于鸿洋大神的玩android开放API完成的《玩android》微信小程序版本，一起来学习小程序开发吧。

### 目前文章详情，使用的是复制链接到剪切板。因为个人小程序不支持打开外部链接。本人也是很无奈啊。没办法，个人的小程序限制太多，如果可以的话，还是尽量搞一个企业账号玩玩吧！我正在准备注册一个“个体工商户”的小程序账户，等注册成功了，再把文章详情的外部链接加上试一试。

### 由于小程序上线必须要求服务器域名只支持https协议，所以我将玩android的api数据在我本人的服务器上转发了一下。转发的接口地址，在最下面。

**小程序目前正在上线审核中...这两天估计就能通过，就可以扫码体验了**

![小程序码](https://github.com/mtjsoft/wanandroid/blob/master/img-folder/gh_de1f6e6fea7e_258.jpg)

![首页](https://github.com/mtjsoft/wanandroid/blob/master/img-folder/%E9%A6%96%E9%A1%B5.png)     ![热搜](https://github.com/mtjsoft/wanandroid/blob/master/img-folder/%E7%83%AD%E6%90%9C.png)

![体系](https://github.com/mtjsoft/wanandroid/blob/master/img-folder/%E4%BD%93%E7%B3%BB.png)     ![我的](https://github.com/mtjsoft/wanandroid/blob/master/img-folder/%E6%88%91%E7%9A%84.png)

![文章列表](https://github.com/mtjsoft/wanandroid/blob/master/img-folder/%E6%96%87%E7%AB%A0%E5%88%97%E8%A1%A8.png)     ![登录](https://github.com/mtjsoft/wanandroid/blob/master/img-folder/%E7%99%BB%E5%BD%95.png)

```
/**
 * 玩android开放api，没有整理，凑合着也能看吧，呵呵
 * 本人服务器域名地址: https://www.mtjsoft.cn
 */
@RestController
@RequestMapping(value = "/wanandroid/api/")
public class WanAndroidApiController {

    /**========================================1.首页相关=================================================================**/
    /**
     * 首页文章列表
     *
     * @param pagernumber 方法：GET
     *                    参数：页码，拼接在连接中，从0开始。
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/article/list")
    public String indexList(@RequestParam(value = "pagernumber") int pagernumber) throws Exception {
        String url = "http://www.wanandroid.com/article/list/" + pagernumber + "/json";
        HttpMethod method = HttpMethod.GET;
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, null);
    }


    /**
     * 首页banner
     *
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/banner")
    public String indexBanner() throws Exception {
        //url
        String url = "http://www.wanandroid.com/banner/json";
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, null);
    }

    /**
     * 常用网站
     *
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/friend")
    public String friend() throws Exception {
        //url
        String url = "http://www.wanandroid.com/friend/json";
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, null);
    }

    /**
     * 搜索热词
     *
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/hotkey")
    public String hotkey() throws Exception {
        //url
        String url = "http://www.wanandroid.com/hotkey/json";
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, null);
    }


    /**========================================2.体系=================================================================**/

    /**
     * 体系数据
     *
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/tree")
    public String tree() throws Exception {
        //url
        String url = "http://www.wanandroid.com/tree/json";
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, null);
    }

    /**
     * 知识体系下的文章
     *
     * @param pagernumber 方法：GET
     *                    参数：
     *                    cid 分类的id，上述二级目录的id
     *                    页码：拼接在链接上，从0开始。
     * @param cid
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/tree/list")
    public String treeList(@RequestParam(value = "pagernumber") int pagernumber, @RequestParam(value = "cid") String cid) throws Exception {
        //url
        String url = "http://www.wanandroid.com/article/list/" + pagernumber + "/json?cid="+cid;
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, null);
    }

    /**========================================3.导航=================================================================**/
    /**
     * 导航数据
     *
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/navi")
    public String navi() throws Exception {

        //url
        String url = "http://www.wanandroid.com/navi/json";
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, null);
    }

    /**========================================4.项目=================================================================**/
    /**
     * 项目分类
     *
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/project")
    public String project() throws Exception {
        //url
        String url = "http://www.wanandroid.com/project/tree/json";
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, null);
    }

    /**
     * 项目列表数据
     *
     * @param pagernumber 方法：GET
     *                    参数：
     *                    cid 分类的id，上面项目分类接口
     *                    页码：拼接在链接中，从1开始。
     * @param cid
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/project/list")
    public String projectList(@RequestParam(value = "pagernumber") int pagernumber, @RequestParam(value = "cid") String cid) throws Exception {
        //url
        String url = "http://www.wanandroid.com/project/list/" + pagernumber + "/json";
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        params.add("cid", cid);
        return HttpClient.init().client(url, method, params, null);
    }

    /**========================================5. 登录与注册=================================================================**/

    /**
     * 登录
     *
     * @param username 方法：POST
     *                 参数：
     *                 username，password
     *                 登录后会在cookie中返回账号密码，只要在客户端做cookie持久化存储即可自动登录验证。
     * @param password
     * @return
     * @throws Exception
     */
    @PostMapping(value = "/login")
    public String login(@RequestParam(value = "username") String username, @RequestParam(value = "password") String password) throws Exception {
        //url
        String url = "http://www.wanandroid.com/user/login";
        //get请求
        HttpMethod method = HttpMethod.POST;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        params.add("username", username);
        params.add("password", password);
        return HttpClient.init().client(url, method, params, username);
    }

    /**
     * 退出登录，清楚本地cookie
     *
     * @param username
     * @throws Exception
     */
    @GetMapping(value = "/loginout")
    public void loginout(@RequestParam(value = "username") String username) throws Exception {
        HttpClient.init().deteleCookie(username);
    }


    /**
     * 注册
     *
     * @param username   方法：POST
     *                   参数
     *                   username,password,repassword
     * @param password
     * @param repassword
     * @return
     * @throws Exception
     */
    @PostMapping(value = "/register")
    public String register(@RequestParam(value = "username") String username, @RequestParam(value = "password") String password
            , @RequestParam(value = "repassword") String repassword) throws Exception {
        //url
        String url = "http://www.wanandroid.com/user/register";
        //get请求
        HttpMethod method = HttpMethod.POST;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        params.add("username", username);
        params.add("password", password);
        params.add("repassword", repassword);
        return HttpClient.init().client(url, method, params, null);
    }

    /**========================================6. 收藏=================================================================**/
    /**
     * 收藏的文章列表
     *
     * @param pagernumber 方法：GET
     *                    参数： 页码：拼接在链接中，从0开始。
     * @return
     * @throws Exception
     */
    @GetMapping(value = "/collect/list")
    public String collectList(@RequestParam(value = "pagernumber") int pagernumber, @RequestParam(value = "username") String username) throws Exception {
        //url
        String url = "http://www.wanandroid.com/lg/collect/list/" + pagernumber + "/json";
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, username);
    }

    /**
     * 收藏站内文章
     *
     * @param id 方法：POST
     *           参数： 文章id，拼接在链接中。
     *           注意链接中的数字，为需要收藏的id.
     * @return
     * @throws Exception
     */
    @PostMapping(value = "/collect")
    public String collect(@RequestParam(value = "id") int id, @RequestParam(value = "username") String username) throws Exception {
        //url
        String url = "http://www.wanandroid.com/lg/collect/" + id + "/json";
        //get请求
        HttpMethod method = HttpMethod.POST;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, username);
    }

    /**
     * 从文章列表取消收藏
     *
     * @param id 方法：POST 参数：
     *           id:拼接在链接上
     * @return
     * @throws Exception
     */
    @PostMapping(value = "/uncollectoriginId")
    public String uncollectoriginId(@RequestParam(value = "id") int id, @RequestParam(value = "username") String username) throws Exception {
        //url
        String url = "http://www.wanandroid.com/lg/uncollect_originId/" + id + "/json";
        //get请求
        HttpMethod method = HttpMethod.POST;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(url, method, params, username);
    }

    /**
     * 从我的收藏页面取消收藏
     *
     * @param id 方法：POST
     *           参数：
     *           id:拼接在链接上
     *           originId:列表页下发，无则为-1
     *           originId 代表的是你收藏之前的那篇文章本身的id； 但是收藏支持主动添加，这种情况下，没有originId则为-1
     * @return
     * @throws Exception
     */
    @PostMapping(value = "/uncollect")
    public String uncollect(@RequestParam(value = "id") int id, @RequestParam(value = "username") String username,
                            @RequestParam(value = "originId") String originId) throws Exception {
        //url
        String url = "http://www.wanandroid.com/lg/uncollect/" + id + "/json";
        //get请求
        HttpMethod method = HttpMethod.POST;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        params.add("originId",originId);
        return HttpClient.init().client(url, method, params, username);
    }

    /**========================================7. 搜索=================================================================**/
    /**
     * 搜索
     *
     * @param key         方法：POST
     *                    参数：
     *                    页码：拼接在链接上，从0开始。
     *                    k ： 搜索关键词
     *                    注意：支持多个关键词，用空格隔开
     * @param pagernumber
     * @return
     * @throws Exception
     */
    @PostMapping(value = "/query")
    public String query(@RequestParam(value = "key") String key, @RequestParam(value = "pagernumber") int pagernumber) throws Exception {
        //url
        String url = "http://www.wanandroid.com/article/query/" + pagernumber + "/json";
        //get请求
        HttpMethod method = HttpMethod.POST;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        params.add("k", key);
        return HttpClient.init().client(url, method, params, null);
    }

    /**========================================8. HTML=================================================================**/
    @GetMapping(value = "/html")
    public String html(@RequestParam(value = "link") String link)throws Exception{
        //get请求
        HttpMethod method = HttpMethod.GET;
        // 封装参数，千万不要替换为Map与HashMap，否则参数无法传递
        MultiValueMap<String, String> params = new LinkedMultiValueMap<String, String>();
        return HttpClient.init().client(link, method, params, null);
    }
}
```
