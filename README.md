# 프로젝트 소개

spring 공식 사이트에서 제공하는 cross-origin설정을 위한 가이드 입니다.
[사이트 바로가기](https://spring.io/guides/gs/rest-service-cors)

---

# 핵심 기능

- 개별 메소드에 적용하는 방법

      @CrossOrigin(origins = "http://localhost:9000")
      @GetMapping("/greeting")
      public Greeting greeting(@RequestParam(required = false, defaultValue = "World")String name) {
          System.out.println("==== get greeting ====");
          return new Greeting(counter.incrementAndGet(), String.format(template, name));
      }

- 전역 설정하는 방법

      @Configuration
      public class WebConfig {
      
          @Bean
          public WebMvcConfigurer corsConfigurer() {
              return new WebMvcConfigurer() {
                  @Override
                  public void addCorsMappings(CorsRegistry registry) {
                      registry.addMapping("/greeting").allowedOrigins("http://localhost:9000");
                  }
              };
          }
      }

  
  
