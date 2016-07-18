## 1. How to open okhttp log ?

### 1. Add in build.gradle
     compile 'com.squareup.okhttp3:logging-interceptor:3.4.1'
## 2. Create HttpLoggingInterceptor and set it to OkHttp Client .
        HttpLoggingInterceptor logging = new HttpLoggingInterceptor();  
        // set your desired log level
        logging.setLevel(HttpLoggingInterceptor.Level.BODY);
        OkHttpClient.Builder httpClient = new OkHttpClient.Builder();   
        // add your other interceptors …
        // add logging as last interceptor
        httpClient.addInterceptor(logging);  // <-- this is the important line!
        Retrofit retrofit = new Retrofit.Builder()  
        .baseUrl(API_BASE_URL)
        .addConverterFactory(GsonConverterFactory.create())
        .client(httpClient.build())
        .build();
