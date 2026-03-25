# -from time import sleep    # 신호 유지를 위한 시간 지연 함수 로드

carLedRed = 2       # 차량용 적색 
carLedYellow = 3    # 차량용 파란색
carLedGreen = 4     # 차량용 녹색
humanLedRed = 20    # 보행자용 적색 
humanLedGreen = 21  # 보행자용 녹색 

carLedRed = LED(2)
carLedYellow = LED(3)
carLedGreen = LED(4)
humanLedRed = LED(20)
humanLedGreen = LED(21)

try:

    while 1:
        carLedRed.value = 0      # 차량 적색 소등
        carLedYellow.value = 0   # 차량 파라색색 소등
        carLedGreen.value = 1    # 차량 녹색 점등 (통행 허용)
        humanLedRed.value = 1    # 보행자 적색 점등 (건너기 금지)
        humanLedGreen.value = 0  # 보행자 녹색 소등
        sleep(3.0)               # 이 상태를 3초간 유지

        carLedRed.value = 0      # 차량 적색 소등 유지
        carLedYellow.value = 1   # 차량 파란색색 점등 (정지 준비)
        carLedGreen.value = 0    # 차량 녹색 소등
        humanLedRed.value = 1    # 보행자 적색 점등 유지
        humanLedGreen.value = 0  # 보행자 녹색 소등 유지
        sleep(1.0)               # 주의 신호를 1초간 유지

        carLedRed.value = 1      # 차량 적색 점등 (정지)
        carLedYellow.value = 0   # 차량 파란색 소등
        carLedGreen.value = 0    # 차량 녹색 소등
        humanLedRed.value = 0    # 보행자 적색 소등
        humanLedGreen.value = 1  # 보행자 녹색 점등 (건너기 허용)
        sleep(3.0)               # 보행 시간을 3초간 유지
    
except KeyboardInterrupt:
    # 사용자가 Ctrl+C를 눌러 종료했을 때 발생하는 예외 처리
    pass

# [Step 4] 리소스 해제 및 안전 종료 (모든 LED 소등)
# 프로그램 종료 후에도 전압이 남아 LED가 켜져 있는 것을 방지
carLedRed.value = 0
carLedYellow.value = 0
carLedGreen.value = 0
humanLedRed.value = 0
humanLedGreen.value = 0
